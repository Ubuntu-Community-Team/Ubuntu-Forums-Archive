---
title: "Vmware:  Want to install Fedora Core 5"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by dwhitney67 on 2007-06-28
I installed Vmware Server and using the console, I have "powered up" an install of Fedora Core 5.

I am at the point were FC5 wants to set up partitions on my sda device.  That is the same device on which I have ubuntu installed.  I do not have an spare partitions on that device.

What is the next step should I take... do I abort the installation of FC5, or do I let it have access to sda?  I certainly do not want to lose my Ubuntu!

I should point out my primary OS is Ubuntu 7.04 Feisty.

---

### Post by ryanVickers on 2007-06-28
Before you go any further, I would remove VMware and get VirtualBox - it runs 100% as fast as the "real" operation system desired, (unlike VMware, even with VMtools, is like 5 to 30% at best I think!) and the features are quite nice!

---

### Post by PilotJLR on 2007-06-28
> **dwhitney67 said:**
> I installed Vmware Server and using the console, I have "powered up" an install of Fedora Core 5.

I am at the point were FC5 wants to set up partitions on my sda device.  That is the same device on which I have ubuntu installed.  I do not have an spare partitions on that device.

What is the next step should I take... do I abort the installation of FC5, or do I let it have access to sda?  I certainly do not want to lose my Ubuntu!

I should point out my primary OS is Ubuntu 7.04 Feisty.

Continue and allow it to partition the disk. Keep in mind your "virtual" /dev/sda is NOT the same as your physical one. Note that Fedora's anaconda installer will even say that no partitions exist on the disk, which proves the point.
Start to think in virtualization terms.  :-)
You now have a virtual disk, which is merely some files on your host OS (ubuntu)... while the "guest" merely thinks it has a real hard disk.


And VirtualBox uses full virtualization, like VMware Server/Workstation. I personally have not observed a performance difference between the two. Just what I've seen thus far... I have used all VMware products extensively at work.

---

### Post by dwhitney67 on 2007-06-29
PilotJLR - Thanks for the clarification concerning virtualization.  I allocated an 8GB space for FC5, but when I saw that it wanted to use /dev/sda I had to pause for a moment to reflect upon what was going on.  I will proceed forward.  Whew... I was worried there for a while.  :)

ryanVickers - I have multiple systems to play with, so perhaps I will test the VirtualBox.  I just hope it is easy to install.  Do you have a URL of where I may find a "HowTo" document?

---

### Post by farmera2005 on 2007-06-29
One thing I have had luck with when installing Fedora under VMWare is to create the hard disk as an IDE and not a SCSI drive.

You can do this by selecting Custom when it asks.

If you have any questions, feel free to emai me at [email]afarmer@farmernetworks.com[/email] - I have done a lot of vmware work under Ubuntu.

Adam

---

