---
title: "VMWare / Nic Issues"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by ielliott on 2006-08-24
I am having trouble i'm running Vmware in Windows, and i'm trying out Ubuntu, but for some reason its not detecting my nic card on boot. The install worked fine so i have no idea why it wouldn't show up now (I'm assuming the install had to connect to the internet)

Any Reason why? I'm new to VMWare

---

### Post by Marsolin on 2006-08-24
Do you happen to have multiple network cards?  I'm tying this reply using a Debian Etch VM running on VMware Player on my Windows XP based laptop at work. I found that I have to run vmnetcfg.exe and select a specific NIC for VMnet0 from the Host Virtual Network Mapping tab.

Also make sure that Ethernet is connected when looking at the VMware settings.

Finally, I frequently need to initialize my network from the command line in the VM. For that I run "sudo ifup eth0". This will enable it and look for a DHCP server to get an IP address.

---

