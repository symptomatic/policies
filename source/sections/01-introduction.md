# 1. Introduction

Symptomatic, Inc ("Symptomatic") is committed to ensuring the confidentiality, privacy, integrity, and availability of all electronic protected health information (ePHI) it receives, maintains, processes and/or transmits on behalf of its Customers. As stewards of compliant, hosted infrastructure used by health technology vendors, developers, designers, agencies, custom development shops, and enterprises, Symptomatic strives to maintain compliance, proactively address information security, mitigate risk for its Customers, and assure known breaches are completely and effectively communicated in a timely manner. The following documents address core policies used by Symptomatic to maintain compliance and assure the proper protections of infrastructure used to store, process, and transmit ePHI for Symptomatic Customers.

Symptomatic provides secure and compliant cloud-based software, consumer apps, and blockchain management. This hosted software falls into two broad categories: 1) **Platform as a Service (PaaS)**, 2) **Platform Add-ons**, 3) **Consumer Apps**, and 4) **Blockchain Management**. These Categories are cited throughout polices as Customers in each category inherit different policies, procedures, and obligations from Symptomatic.

## 1.1 Platform as a Service (PaaS)

PaaS Customers utilize hosted software and infrastructure from Symptomatic to deploy, host, and scale custom developed applications and configured databases. These customers are deployed into compliant containers run on systems secured and managed by Symptomatic. Symptomatic does not have insight or access into application level data of PaaS Customers and, as such, does not have the ability to secure or manage risk associated with application level vulnerabilities and security weaknesses. Symptomatic makes every effort to reduce the risk of unauthorized disclosure, access, and/or breach of PaaS Customer data through network (firewalls, dedicated IP spaces, etc) and server settings (encryption at rest and in transit, OSSEC throughout the Platform, etc).

PaaS Customers can opt for a list of Services from Symptomatic, which include Backup Service, Logging Service, IDS Service, and Disaster Recovery Service. These services are not standard and PaaS Customers must sign up for them in order for Symptomatic to manage these areas of security and compliance.

## 1.2 Platform Add-ons

Add-ons are compliant API-driven services that are offered as part of the Symptomatic Platform. These services currently include our Backend as a Service and secure Messaging Service. With Add-ons, Symptomatic has access to data models and manages all application level configurations and security.

In the future there may be 3rd party Add-on services available as part of the Symptomatic Platform. These 3rd party, or Partner, Services will be fully reviewed by Symptomatic to assure they do not have a negative impact on Symptomatic's information security and compliance posture.

## 1.3 Consumer Apps

To be specified.

## 1.4 Blockchain Management

To be specified.


## 2.1 Compliance Inheritance

Symptomatic signs business associate agreements (BAAs) with its Customers. These BAAs outline Symptomatic obligations and Customer obligations, as well as liability in the case of a breach. In providing infrastructure and managing security configurations that are a part of the technology requirements that exist in HIPAA and HITRUST, as well as future compliance frameworks, Symptomatic manages various aspects of compliance for Customers. The aspects of compliance that Symptomatic manages for Customers are inherited by Customers, and Symptomatic assumes the risk associated with those aspects of compliance. In doing so, Symptomatic helps Customers achieve and maintain compliance, as well as mitigates Customers risk.

Symptomatic does not act as a covered entity. When Symptomatic does operate as a business associate (not a subcontractor), Symptomatic does not interface with users to obtain or provide access to ePHI. Access to ePHI is through our customers' applications.

Certain aspects of compliance cannot be inherited. Because of this, Symptomatic Customers, in order to achieve full compliance or HITRUST Certification, must implement certain organizational policies. These policies and aspects of compliance fall outside of the services and obligations of Symptomatic.

Mappings of HIPAA Rules to Symptomatic controls and a mapping of what Rules are inherited by Customers, both Platform Customers and Add-on Customers, are covered in [§2](#2.-hipaa-inheritance).

## 1.4 Symptomatic Organizational Concepts

The physical infrastructure environment is hosted at [Amazon Web Services](https://aws.amazon.com/) (AWS) and [Microsoft Azure](https://azure.microsoft.com/), and [IBM SoftLayer](http://www.softlayer.com/). The network components and supporting network infrastructure are contained within the AWS, Azure, and SoftLayer infrastructures and managed by AWS, Microsoft, and IBM (respectively). Symptomatic does not have physical access into the network components. The Symptomatic environment consists of Cisco firewalls; nginx web servers; Node application servers; MongoDB database servers; Linux Ubuntu monitoring servers; Windows Server virtual machines; Docker containers; and developer tool servers running on Linux Ubuntu.

Within the Symptomatic Platform on AWS, Azure, and SoftLayer, all data transmission is encrypted and all hard drives are encrypted so data at rest is also encrypted; this applies to all servers - those hosting Docker containers, databases, APIs, log servers, etc. Symptomatic assumes all data *may* contain ePHI, even though our Risk Assessment does not indicate this is the case, and provides appropriate protections based on that assumption.

In the case of PaaS and Consumer App Customers, it is the responsibility of the Customer to restrict, secure, and assure the privacy of all ePHI data at the Application Level, as this is not under the control or purview of Symptomatic.  

The data and network segmentation mechanism differs depending on the primitives offered by the underlying cloud provider infrastructure:

* Within AWS, hosted load balancers segment data across dedicated Virtual Private Clouds for PaaS Customers and for Platform Add-ons.
* Within Azure, hosted load balancers segment data across dedicated Virtual Networks for PaaS Customers and for Platform Add-ons.

The result of segmentation strategies employed by Symptomatic effectively create RFC 1918, or dedicated, private segmented and separated networks and IP spaces, for each PaaS Customer and for Platform Add-ons.

Additionally, IPtables is used on each each server for logical segmentation. IPtables is configured to restrict access to only justified ports and protocols. Symptomatic has implemented strict logical access controls so that only authorized personnel are given access to the internal management servers. The environment is configured so that data is transmitted from the load balancers to the application servers over an TLS encrypted session.

In the case of Platform Add-ons, once the data is received from the application server, a series of Application Programming Interface (API) calls is made to the database servers where the ePHI resides. The ePHI is separated into PostgreSQL and Percona databases through programming logic built, so that access to one database server will not present you with the full ePHI spectrum.

The VPN server, nginx web server, and application servers are externally facing and accessible via the Internet. The database servers, where the ePHI resides, are located on the internal Symptomatic network and can only be accessed through a bastion host over a VPN connection. Access to the internal database is restricted to a limited number of personnel and strictly controlled to only those personnel with a business-justified reason. Remote access to internal servers is not accessible except through load balancers.

All Platform Add-ons and operating systems are tested end-to-end for usability, security, and impact prior to deployment to production.

## 1.5 Requesting Audit and Compliance Reports

Symptomatic, at its sole discretion, shares audit reports, including its HITRUST reports and Corrective Action Plans (CAPs), with customers on a case by case basis. All audit reports are shared under explicit NDA in Symptomatic format between Symptomatic and party to receive materials. AuditEvent reports can be requested by Symptomatic workforce members for Customers or directly by Symptomatic Customers.

The following process is used to request audit reports:

1. Email is sent to compliance-reports@symptomatic.io. In the email, please specify the type of report being requested and any required timelines for the report.
2. Symptomatic staff will fill out the [Compliance Review Form](https://docs.google.com/forms/d/e/1FAIpQLSfNIu0YFD2Yt4OgOMQPPnSDccG7qX0sXCx7U4hiGE5v4fyS3A/viewform?usp=sf_link) form to include the request in the [Compliance Review Activities Log](https://docs.google.com/spreadsheets/d/1Hcy45pCmEExXnlODVpFOqh9Dv1FXkiGguYGn9BuQxjA/edit?usp=sharing).  
3. Symptomatic will confirm if a current NDA is in place with the party requesting the audit report. If there is no NDA in place, Symptomatic will send one for execution.
4. Once it has been confirmed that an NDA is executed, Symptomatic staff will update the status to "Under Review".
5. The Symptomatic Security Officer or Privacy Officer must Approve or Reject the Issue. If the Issue is rejected, Symptomatic will notify the requesting party that we cannot share the requested report.
4. If the Issue has been Approved, Symptomatic will send the customer the requested audit report.

## 1.6 Version Control

Refer to the GitHub repository at [https://github.com/symptomatic/policies/](https://github.com/symptomatic/policies/) for the full version history of these policies.
