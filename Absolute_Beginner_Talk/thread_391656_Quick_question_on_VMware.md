---
title: "Quick question on VMware"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by cawill on 2007-03-23
Hi, 
I have set up VMware using this guide
[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html")

And when i open the windows.vmdk file i get the following error:

**'Error while opening virtual machine /home/chris/vmware/windows.vmdk: File "/home/chris/vmware/windows.vmdk" line 8: Syntax error.'**

The vmdk file is:

# Disk DescriptorFile

version=1

CID=9428f535

parentCID=ffffffff

createType="fullDevice"



# Extent description

RW 63 FLAT "windowsxp.mbr" 0

RW 390721904 FLAT "/dev/hda" 63 



# The Disk Data Base 

#DDB 



ddb.toolsVersion = "6530"

ddb.adapterType = "ide"

ddb.virtualHWVersion = "4"

ddb.geometry.sectors = "63"

ddb.geometry.heads = "255"

ddb.geometry.cylinders = "24321"


Thanks Chris

---

### Post by zvacet on 2007-03-23
I know this is not maybe a real help but anyway
[http://ubuntuforums.org/showthread.php?t=371246&highlight=vmware]("http://ubuntuforums.org/showthread.php?t=371246&highlight=vmware")

---

