---
title: Default permissions for MachineKeys folders
description: Describes default permissions for the MachineKeys folders.
ms.date: 09/08/2020
author: Deland-Han
ms.author: delhan
manager: dscontentpm
audience: itpro
ms.topic: troubleshooting
ms.prod: windows-server
localization_priority: medium
ms.reviewer: kaushika
ms.prod-support-area-path: Permissions, access control, and auditing
ms.technology: WindowsSecurity
---
# Default permissions for the MachineKeys folders

This article describes default permissions for the MachineKeys folders.

_Original product version:_ &nbsp; Windows Server 2003  
_Original KB number:_ &nbsp; 278381

## Summary

The MachineKeys folder stores certificate pair keys for both the computer and users. Both Certificate services and Internet Explorer use this folder. The default permissions on the folder may be misleading when you attempt to determine the minimum permissions that are necessary for proper installation and the accessing of certificates.

## Default permissions for MachineKeys folder

The MachineKeys folder is located under the `All Users Profile\Application Data\Microsoft\Crypto\RSA` folder. If the administrator did not set the folder to the minimum level, a user may receive the **Failed to Generate Certificate Request** and **Internal Server Error** (The Private Key that you are importing might require a cryptographic service provider that is not installed on your system) when the user generates a server certificate by using Microsoft Internet Information Server (IIS). The following settings are the default permissions for the MachineKeys folder:

- Administrators (Full Control) This folder only
- Everyone (Special) This folder only

## Permissions for Everyone group

To view the special permissions for the Everyone group, right-click the **MachineKeys** folder, click **Advanced** on the **Security** tab, and then click **View/Edit**. The permissions consist of the following permissions:

- List Folder/Read Data
- Read Attributes
- Read Extended Attributes
- Create Files/Write Data
- Create Folders/Append Data
- Write Attributes
- Write Extended Attributes
- Read Permissions

Select the **Reset Permissions on all Child objects and enable propagation of inheritable permissions** check box. The administrator does not have full control on child objects to protect a user's private part of the key pair. However, the administrator can still delete certificates for a user.

For more information, see [How to set required NTFS permissions and user rights for an IIS 5.0, IIS 5.1, or IIS 6.0 Web server](https://support.microsoft.com/help/271071).