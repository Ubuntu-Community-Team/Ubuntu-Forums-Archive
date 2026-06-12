---
title: "virtual box, Help!"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Navoj on 2008-01-31
I'm launching  Virtual box but getting this.


Could not load the settings file '/home/navoj/.VirtualBox/VirtualBox.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Attribute 'LogHistoryCount' is not declared for element 'SystemProperties'
Location: '/home/navoj/.VirtualBox/VirtualBox.xml', line 25, column 159.


Result Code: 
0x80004005
Component: 
VirtualBox
Interface: 
IVirtualBox {76b25f3c-15d4-4785-a9d3-adc6a462beec}

 how can I fix it?

---

### Post by heathguy on 2008-02-01
You could edit that file (VirtualBox.xml) and add LogHistoryCount="3" into the <SystemProperties.../> line

For example mine looks like this:

<SystemProperties HWVirtExEnabled="false" LogHistoryCount="3" defaultMachineFolder="Machines" defaultVDIFolder="VDI" remoteDisplayAuthLibrary="VRDPAuth"/>

Hope this helps.

--Heath

---

