[comment]: # "Auto-generated SOAR connector documentation"
# Forcepoint Web Security

Publisher: Splunk Community  
Connector Version: 2\.0\.1  
Product Vendor: Forcepoint  
Product Name: Web Security  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 5\.0\.0  

This app provides category management and blocking actions for the Forcepoint Web Security platform

### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Web Security asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**base\_url** |  required  | string | Hostname
**port** |  required  | numeric | Port \(Forcepoint default\: 15873\)
**verify\_server\_cert** |  optional  | boolean | Verify server certificate
**ph\_0** |  optional  | ph | 
**username** |  required  | string | User Name
**password** |  required  | password | Password

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using supplied configuration  
[block ip](#action-block-ip) - Block IP or list of IPs by adding them to the supplied category  
[block url](#action-block-url) - Block URL or list of URLs by adding them to the supplied category  
[unblock ip](#action-unblock-ip) - Unblock IP or list of IPs by removing them from the supplied category  
[unblock url](#action-unblock-url) - Unblock URL or list of URLs by removing them from the supplied category  
[lookup ip](#action-lookup-ip) - Lookup the categories related to the IP or list of IPs  
[lookup url](#action-lookup-url) - Lookup the categories related to the URL or list of URLs  
[get category](#action-get-category) - Return the category list contents  
[list categories](#action-list-categories) - Return a list of all API\-managed categories  
[delete category](#action-delete-category) - Delete API\-managed category  
[add category](#action-add-category) - Add API\-managed category to Forcepoint  

## action: 'test connectivity'
Validate the asset configuration for connectivity using supplied configuration

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'block ip'
Block IP or list of IPs by adding them to the supplied category

Type: **contain**  
Read only: **False**

Adding an IP to a category automatically sets it into a blocking action\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**ip** |  required  | IP or list of IPs to block | string |  `ip` 
**category** |  required  | Add the IP\(s\) to this category | string |  `forcepoint category` 
**create\_category** |  optional  | If the category does not exist, create it | boolean | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.category | string |  `forcepoint category` 
action\_result\.parameter\.create\_category | boolean | 
action\_result\.parameter\.ip | string |  `ip` 
action\_result\.data\.\*\.Category ID | numeric | 
action\_result\.data\.\*\.Category Name | string |  `forcepoint category` 
action\_result\.data\.\*\.Totals\.Added IPs | numeric | 
action\_result\.data\.\*\.Totals\.Added URLs | numeric | 
action\_result\.summary\.category | string |  `forcepoint category` 
action\_result\.summary\.transaction\_id | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'block url'
Block URL or list of URLs by adding them to the supplied category

Type: **contain**  
Read only: **False**

Adding URLs to a category automatically sets it into a blocking action\.<br />NOTE\: If a url is provided without the protocol, it will block HTTP, HTTPS, and FTP\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**url** |  required  | URL or list of URLs to block | string |  `url`  `domain` 
**category** |  required  | Add the URL\(s\) to this category | string |  `forcepoint category` 
**create\_category** |  optional  | If the category does not exist, create it | boolean | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.category | string |  `forcepoint category` 
action\_result\.parameter\.create\_category | boolean | 
action\_result\.parameter\.url | string |  `url`  `domain` 
action\_result\.data\.\*\.Category ID | numeric | 
action\_result\.data\.\*\.Category Name | string |  `forcepoint category` 
action\_result\.data\.\*\.Totals\.Added IPs | numeric | 
action\_result\.data\.\*\.Totals\.Added URLs | numeric | 
action\_result\.summary\.category | string |  `forcepoint category` 
action\_result\.summary\.transaction\_id | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'unblock ip'
Unblock IP or list of IPs by removing them from the supplied category

Type: **correct**  
Read only: **False**

An empty category will remove them from all available categories\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**ip** |  required  | IP or list of IPs to unblock | string |  `ip` 
**category** |  optional  | Category for which to remove the block \(if empty, remove from all categories\) | string |  `forcepoint category` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.category | string |  `forcepoint category` 
action\_result\.parameter\.ip | string |  `ip` 
action\_result\.data\.\*\.Category ID | numeric | 
action\_result\.data\.\*\.Category Name | string |  `forcepoint category` 
action\_result\.data\.\*\.IPs | string |  `ip` 
action\_result\.data\.\*\.Totals\.Deleted IPs | numeric | 
action\_result\.data\.\*\.Totals\.Deleted URLs | numeric | 
action\_result\.data\.\*\.Transaction ID | string | 
action\_result\.summary\.commit\_time | string | 
action\_result\.summary\.transaction\_id | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'unblock url'
Unblock URL or list of URLs by removing them from the supplied category

Type: **correct**  
Read only: **False**

An empty category will remove them from all available categories\.<br />NOTE\: If a url is provided without the protocol, it will unblock HTTP, HTTPS, and FTP\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**url** |  required  | URL or list of URLs to unblock | string |  `url`  `domain` 
**category** |  optional  | Category for which to remove the block \(if empty, remove from all categories\) | string |  `forcepoint category` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.category | string |  `forcepoint category` 
action\_result\.parameter\.url | string |  `url`  `domain` 
action\_result\.data\.\*\.Category ID | numeric | 
action\_result\.data\.\*\.Category Name | string |  `forcepoint category` 
action\_result\.data\.\*\.Totals\.Deleted IPs | numeric | 
action\_result\.data\.\*\.Totals\.Deleted URLs | numeric | 
action\_result\.data\.\*\.Transaction ID | string | 
action\_result\.data\.\*\.URLs | string | 
action\_result\.summary\.commit\_time | string | 
action\_result\.summary\.transaction\_id | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'lookup ip'
Lookup the categories related to the IP or list of IPs

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**ip** |  required  | IP or list of IPs to lookup | string |  `ip` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.ip | string |  `ip` 
action\_result\.data\.\*\.categories | string |  `forcepoint category` 
action\_result\.data\.\*\.ip | string |  `ip` 
action\_result\.summary\.found category count | numeric | 
action\_result\.summary\.lookup count | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'lookup url'
Lookup the categories related to the URL or list of URLs

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**url** |  required  | URL or list of URLs to lookup | string |  `url` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.url | string |  `url` 
action\_result\.data\.\*\.categories | string |  `forcepoint category` 
action\_result\.data\.\*\.url | string |  `url` 
action\_result\.summary\.found category count | numeric | 
action\_result\.summary\.lookup count | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get category'
Return the category list contents

Type: **investigate**  
Read only: **True**

Return all URLs and IPs in a specified category\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**category** |  required  | Category name | string |  `forcepoint category` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.category | string |  `forcepoint category` 
action\_result\.data\.\*\.ip | string |  `ip` 
action\_result\.data\.\*\.url | string |  `url` 
action\_result\.summary\.category\_id | numeric | 
action\_result\.summary\.category\_name | string |  `forcepoint category` 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list categories'
Return a list of all API\-managed categories

Type: **investigate**  
Read only: **True**

Only API\-managed categories can be viewed or changed\.

#### Action Parameters
No parameters are required for this action

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.data\.\*\.Category Description | string | 
action\_result\.data\.\*\.Category Hierarchy | numeric | 
action\_result\.data\.\*\.Category ID | numeric | 
action\_result\.data\.\*\.Category Name | string |  `forcepoint category` 
action\_result\.data\.\*\.Category Owner | string | 
action\_result\.summary\.category count | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'delete category'
Delete API\-managed category

Type: **generic**  
Read only: **False**

Only API\-managed categories can be viewed or changed\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**category** |  required  | Category name | string |  `forcepoint category` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.category | string |  `forcepoint category` 
action\_result\.data\.\*\.category | string | 
action\_result\.summary\.commit\_time | string | 
action\_result\.summary\.transaction\_id | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'add category'
Add API\-managed category to Forcepoint

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**category** |  required  | Category name, must be unique | string |  `forcepoint category` 
**description** |  optional  | Description of the category | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.category | string |  `forcepoint category` 
action\_result\.parameter\.description | string | 
action\_result\.data\.\*\.Categories\.\*\.Category Name | string |  `forcepoint category` 
action\_result\.summary\.commit\_time | string | 
action\_result\.summary\.transaction\_id | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 