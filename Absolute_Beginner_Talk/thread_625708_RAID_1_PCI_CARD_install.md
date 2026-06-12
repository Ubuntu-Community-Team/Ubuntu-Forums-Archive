---
title: "RAID 1 PCI CARD install"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by davidexe on 2007-11-28
OK, onward and upward..  I have the server working for the most part. Now I need to get the RAID 1 working. I found out the PCI SATA controller card I have is supposed to have RAID 1.  It is a VIA6421 and the disk supplied has a linux area that has drivers (but none for Ubuntu).  I did not have the disk in the CD when it was set up and installed but the card was in since before beginning to install Ubuntu Server.  I can see the VIA6421 in the Device Manager.  

I am very familar with installing drivers, etc. in Windows but a complete NOOB when it comes to Linux.  Can someone help me get going?  I am at a point I don't even know the right questions to ask.  How can I check to see if the RAID support is already installed. I am using the drives (two  500 gb) so the card is working to that level.  

HELP???

Thanks in advance for any help.

---

### Post by jviscosi on 2007-11-28
If it's true hardware RAID then in theory I think it should be transparent to Linux.  Mine is (using a 3Ware 7006).  Maybe see if the CD has a monitoring program on it for Linux that you could use to view the status of the array?

---

### Post by davidexe on 2007-11-28
I can find some linux drivers under ITERAID.  I don't know what that is.  But there is nothing that refers to Ubuntu.  There is Red Hat, SUSE, etc. but not Ubuntu.

This is an ultra cheap card. Maybe I should go to a higher end card that is specific for RAID 1 and compatible with Ubuntu?  Does anyone know of such a card?

Thanks.

---

### Post by overdrank on 2007-11-28
> **davidexe said:**
> I can find some linux drivers under ITERAID.  I don't know what that is.  But there is nothing that refers to Ubuntu.  There is Red Hat, SUSE, etc. but not Ubuntu.

This is an ultra cheap card. Maybe I should go to a higher end card that is specific for RAID 1 and compatible with Ubuntu?  Does anyone know of such a card?

Thanks.

Maybe this can help
[http://hardware4linux.info/type/39/](http://hardware4linux.info/type/39/)
Good luck!

---

