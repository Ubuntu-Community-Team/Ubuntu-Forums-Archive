---
title: "Partitioning Ubuntu 10"
date: 2010-06-15
forum: Apple Hardware Users
---

### Post by constantgamer247 on 2010-06-15
Was not sure if I should post this in the mac section because I am installing it on my imac but it's less a mac question and more how do I partition it.


I am trying to make my iMac dual bootable with mac os x and ubuntu 10.

Just wondering if I should use rEFIT?

And should I partition my HDD with boot camp or should I use the partition tools in ubuntu. Also I will be creating a separate partitions for Ubuntu's /home and /root directories

if anyone thinks this should be in the apple section please tell me

---

### Post by r-mo on 2010-06-15
Have you seen this page? it's a pretty detailed guide.

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

You shouldn't have a problem with separate partitions for / and /root just make sure you put grub in the right place on the advanced screen.

---

### Post by srs5694 on 2010-06-15
There's little or no reason to put /root on its own partition, and lots of reason to *not* do this. The /root directory is the home directory for the root user, and it's generally kept on the (confusingly named, in this context) root directory ("/") so that the root user can log into the system even if there are problems mounting other partitions. (Since Ubuntu doesn't permit direct root logins by default, this may not be a big deal for a typical Ubuntu install, but it could be if you change it.)

I suspect you really mean that you want a separate /boot partition. This directory typically contains the Linux kernel and boot loader (GRUB) configuration files. It's sometimes split off from the root ("/") partition as a way of isolating it, making it accessible to boot loader run-time code when using RAID or LVM, or for other reasons.

---

### Post by varunendra on 2010-06-15
> **r-mo said:**
> Have you seen this page? it's a pretty detailed guide.

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

You shouldn't have a problem with separate partitions for / and /root just make sure you put grub in the right place on the advanced screen.

I think no more guidance is needed after following r-mo's link. Mark the thread as [solved] if you are satisfied.

---

### Post by JohnAtilano on 2010-06-16
> **varunendra said:**
> I think no more guidance is needed after following r-mo's link. Mark the thread as [solved] if you are satisfied.

I would be careful about following those instructions.  I believe they are incorrect.

You need to manually create your partitions before you begin the installation process.  Otherwise GRUB will be installed to /dev/sda and it will nuke your system (this happened to me twice).

Use GParted to create your ubuntu and SWAP partitions then execute the install.

---

