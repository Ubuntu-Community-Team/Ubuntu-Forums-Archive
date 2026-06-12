---
title: "macbook x86 wireless"
date: 2007-05-16
forum: Apple Intel Users
---

### Post by nitrofurano on 2007-05-16
how can i configure Ubuntu 7.04 i386 to use wireless (wifi) connections?

---

### Post by mustang on 2007-05-16
Please try to keep all your questions to one thread in the future.

First tell us which generation macbook you have. It should work out of the box for the first generation macbooks. For second generation, you will need ndiswrapper (or you could try the non-ndiswrapper solution--search for the thread)

---

### Post by ronocdh on 2007-05-17
> **mustang said:**
> Please try to keep all your questions to one thread in the future.

First tell us which generation macbook you have. It should work out of the box for the first generation macbooks. For second generation, you will need ndiswrapper (or you could try the non-ndiswrapper solution--search for the thread)
Always recommend MadWifi first!

---

### Post by James_M on 2007-05-17
the latest experimental build of madwifi works for me.  I installed it last night and I love it; works perfectly.  You can find that build [here](http://madwifi.org/wiki/news/20070328/experimental-support-for-ar5008-802-11n)

Before you download that, you should open up a Terminal and type ```
sudo aptitude install build-essential 
``` just to install the frameworks needed for you to install applications like that.  After that, just cd to the directory you extracted the madwifi files to and type in ```
sudo uninstall
``` a few times.  After that, you can type in ```
sudo make
``` Some code will scroll for a second, then you can type in ```
sudo make install
```  That will then install madwifi.  Just reboot and you should have wireless capability.  Mind you, this only works with Core 2 Duo MacBooks to the best of my knowledge.  Core Duo MacBooks work out of the box in my experience.  I tried all these steps last night, and in less than half an hour, I had wireless.  That's gotta be a new record for semi-manual configuration of it.  GUI works too...it's nice...

---

### Post by ronocdh on 2007-05-17
> **James_M said:**
> Mind you, this only works with Core 2 Duo MacBooks to the best of my knowledge.  Core Duo MacBooks work out of the box in my experience.  I tried all these steps last night, and in less than half an hour, I had wireless.  That's gotta be a new record for semi-manual configuration of it.  GUI works too...it's nice...
Yup, worked for me! C2D MBP. Thanks for the handy guide, James. =)

---

### Post by ivesjd on 2007-05-23
I have a first gen macbook, and wireless worked out of the box. But it drops a lot. Its got a decent signal, (around 50%). Its a campus apartment so i have no access to the router, but i do know it is wireless b, no g or n. Im trying to install madwifi thinking it may help. But so far, seems pretty much the same

---

### Post by ronocdh on 2007-05-23
> **ivesjd said:**
> I have a first gen macbook, and wireless worked out of the box. But it drops a lot. Its got a decent signal, (around 50%). Its a campus apartment so i have no access to the router, but i do know it is wireless b, no g or n. Im trying to install madwifi thinking it may help. But so far, seems pretty much the same
IIRC, the first gen MBs don't have Atheros chipsets for wireless. (MadWifi is made specifically for the Atheros cards.) You can check by doing **sudo update-pciids** and then **lspci**. Your wireless card will be near the bottom of the list.

---

### Post by ivesjd on 2007-05-23
Thats what Ive read as well, and I know its a first gen, got it in september.

01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

theres the read out, wireless worked out of the box with a fresh feisty install, but get random drops and reconnects and madwifi is installed, not sure if its being used or not, (forgot how to enable it)

im a student, and we get our laptops through the school, they may have replaced the wifi card during one of the times ive brought it in (have been plagued with bad keyboards)

---

### Post by clcaus on 2007-05-23
I recently recompiled my kernel to get suspend to work (as described in the Ubuntu Macbook Wiki). Now Mad Wifi doesn't work (neither does ndiswrapper). Here's the error message:

```
cd: 1: can't cd to /lib/modules/2.6.20-15-e83-generic/build
Makefile.inc:66: *** /lib/modules/2.6.20-15-e83-generic/build is missing, please set KERNELPATH.  Stop.

```

Any suggestions?

EDIT: Got it working by specifying the path to my headers files. However, now I get the following:

```
Checking requirements... ok.
Checking kernel configuration... FAILED
Please enable wireless extensions.
make: *** [configcheck] Error 1
```

---

### Post by clcaus on 2007-05-24
OK I'm up and running. I just had to edit GRUB.

---

### Post by ivesjd on 2007-05-24
Okay, so after a reinstall, I noticed that the restricted drivers manager uses the Atheros drivers. So I installed madwifi and disabled the Atheros drivers. Then reboot. Wireless works, but I dont know if its using the madwifi or Atheros. In the restricted driver manager it still says they are in use even after I rebooted.

---

