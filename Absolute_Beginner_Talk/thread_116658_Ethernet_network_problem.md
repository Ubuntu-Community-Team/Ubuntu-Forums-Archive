---
title: "Ethernet network problem"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by jph on 2006-01-13
I have just installed Ubuntu 5.10.  After some difficulty, I have it up and runnung.  I can only randomly get on my windows ethernet network, which is a peer to peer workgroup called "workgroup."  Sometimes when I go to Places-Network Servers I see the "workgroup" icon (along with one for "MSHOME") and I'm fine.  However, overwhelmingly I get a box for "Authentication Required" which is asking for my password to login to the domain MSHOME.  There is no such domain.  If I click cancel I see an icon called "Windows Network."  If I click it, it is empty.  I have deactivated and reactivated the ethernet connection in network settings and reinstalled Samba.    Problem persists.  Ethernet properties are for DHCP configuration.  Host settings are hostname: ubuntu and Domain Name is blank.  3 DNS servers are listed and seven host are listed with IP addresses and aliases.  Ubuntu is accessing the network fine because I am able to connect to the internet through the linksys router to the cable modem.  Help would be appreciated.  Thanks. Jim

---

### Post by Iowan on 2006-01-13
By default, Ubuntu sets itself up for workgroup MSHOME  - as does the default SAMBA setup (/etc/samba/smb.conf).  Did you change workgroup in both places?

I may be thinking of an XP install - as I'm trying to install both on one machine...

---

### Post by jph on 2006-01-13
Iowan,
I do not know how to change from MSHOME in either Samba or Ubuntu.  Jim

---

### Post by Iowan on 2006-01-13
Under System>Administration>Networking is a dialog box with General tab.  You can edit the name and domain (workgroup?) from there.  Wish I knew where that info gets stored - as my Ubuntu server doesn't have the GUI.

Under Applications>Accessories is a Text editor. You can use it to Open>Filesystem>etc/samba/smb.conf. Down about line 27 is a workgroup=MSHOME line that can be changed to workgroup=workgroup to put Samba in the same group as your other machines.

Bear in mind that I'm a rookie at Ubuntu, and there may be easier (and/or better) ways to accomplish the task.

---

### Post by jph on 2006-01-14
I don't know why this worked but it did.  I can now get to all the computers on my windows workgroup from my ubuntu machine and see the ubuntu macine from the windows computers.  Here's what I did:  Sysytem - Adminstration - Share Folder- changed "Domain/Workgroup" from "MS/HOME to Workgroup (capital W).  Then Administration - Network Settings - Ethernet- Properties - changed from DHCP to static IP address - entered an IP address at the upper range of the routers settings (to avoid conflicts)- filled in appropriate subnet (it was automatic) and Gateway addresses.  I then rebooted and - voila -I could see all my windows machines in the workgroup and they could see my ubuntu machine.  I still can't access files on the unbuntu machine from the windows machines but I'm working on that.  I get file access from the ubuntu machine to all the windows machines.  
Thanks for your help.  Jim

---

