---
title: "Macbook dkms and bcmwl install"
date: 2015-12-26
forum: Apple Hardware Users
---

### Post by Raphael_Baron on 2015-12-26
Hello, 
I'm sorry to post about this but I've had some major issues with this and haven't found any solutions yet.
I have a macbook pro 2009 BCM4322

I've tried installing the dkms and bcmwl packages offline and with ethernet cable but I keep getting the same problems.
This is what I'm getting :

dpkg: error processing package dkms (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 dkms

:~/Desktop$ sudo dpkg -i bcmwl*.deb
(Reading database ... 197031 files and directories currently installed.)
Preparing to unpack bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu2_i386.deb ...
Unpacking bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) over (6.30.223.141+bdcom-0ubuntu2) ...
dpkg: dependency problems prevent configuration of bcmwl-kernel-source:
 bcmwl-kernel-source depends on dkms.

dpkg: error processing package bcmwl-kernel-source (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bcmwl-kernel-source

I've tried to install it with the software center too but it doesn't work.
Going into the software and updates in system settings doesn't work either. It only works when I use my live usb key
I hope someone can help,
Thank you

Raphael

---

### Post by howefield on 2015-12-26
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by este.el.paz on 2015-12-28
@R_B:

I have an 09 spec MBPro . . . and I've had numerous 'buntu distros installed on it, now running LM 17.2 . . . .  I think you are doing it "the hard way" trying to install the "parts" . . . but, couple questions, you said "Software Center" . . . did you find the "additional drivers" tab and try to install the "Broadcom driver" that way???  I'm pretty sure 14.04 LTS had that feature, in LM it is its own app, and very easy to get the wifi set up, so that is other question, what version/distro are you using?

I'm away from my MBPro right now, but later today I'll be using it and could check some stuff out, but, mainly try to use "Additional Drivers" . . . it should list the "Nvidia" video card drivers, and then at the bottom of the page, should show "Broadcom xxxx???" . . . that will be the wifi card driver.  Should work.

e.

---

### Post by MikeBraxner on 2015-12-29
@Raphael_Baron ... Given your description, I'm not quite sure what exactly your problem is. Let me offer some suggestions/questions to help clarify things.

First, if you have a working ethernet connection --- I assume you do, since you mentioned it, i.e. you can access the Internet with Firefox or the like ... right? --- then forget the dpkg-stuff, and just keep things simple. Make sure you have all repositories activated, including the "Proprietary Drivers" and "restricted" ones, and just try ...
```
sudo apt-get update; sudo apt-get install bcmwl-kernel-source
```

If you ***do not*** have a ***live*** connection ***now***, but ***used one during install*** to download updates, then you are likely looking at a number of versioning-mismatches in the dependency lists, say, between your updated kernel, and the install medium available version of, say, the kernel-sources. Three options: (i) Flatten the system and re-install (this time *without* updates!!); (ii) download the required dependencies by hand, and install them by hand; (iii) get a live connection (ethernet, bluetooth, dongle) and use that to download what you need.

Finally, if you did not download updates while installing the system, and have no live connection available, then [this previous post]("http://ubuntuforums.org/showthread.php?t=2305509&p=13404018#post13404018") should help you sort things out in a jiffy.

---

### Post by dellboy56 on 2016-01-02
Hello author of this thread your in luck i have the same broadcom driver as you heres how to get the wifi working pkug in your usb/cd into your drive and go to pool/mains/d/dkms install the .deb file then backtrack to pools restricted bcmwl and install prompt you that wifi networks are showing hope you enjoy cheers:D

---

