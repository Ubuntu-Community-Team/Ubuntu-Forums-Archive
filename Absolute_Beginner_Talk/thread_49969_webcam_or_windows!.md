---
title: "webcam or windows!"
date: 2005-07-18
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-07-18
Right. I NEED my webcam working now. I have tried aMSN and that killed GAIM so I am not IMless.

I need to get GAIM working again and I need an IM client with webcam support.

I also need to get a driver for my webcam. Is there a generic webcam driver I can use?

---

### Post by damonw5 on 2005-07-18
[QUOTE=gammyhand]Right. I NEED my webcam working now. I have tried aMSN and that killed GAIM so I am not IMless.

I need to get GAIM working again and I need an IM client with webcam support.

I also need to get a driver for my webcam. Is there a generic webcam driver I can use?[/QUOTE]
 What webcam do you have?

To get GAIM working again, go to System->Adminstration->SynapticPackageManager, Search for Gaim, click on the box to the left of the package name and choose reinstall (or install if it was accidentally uninstalled)

---

### Post by gammyhand on 2005-07-18
[QUOTE=damonw5]What webcam do you have?

To get GAIM working again, go to System->Adminstration->SynapticPackageManager, Search for Gaim, click on the box to the left of the package name and choose reinstall (or install if it was accidentally uninstalled)[/QUOTE]
 I have reinstalled it several times. The problem is it just hangs at "retrieving buddy list". It was fine until I installed aMSN. I don't know what the camera is, it is a cheap no-brand one. That is why I need a generic driver.

---

### Post by poofyhairguy on 2005-07-18
[QUOTE=gammyhand]Right. I NEED my webcam working now. I have tried aMSN and that killed GAIM so I am not IMless.

I need to get GAIM working again and I need an IM client with webcam support.

I also need to get a driver for my webcam. Is there a generic webcam driver I can use?[/QUOTE]

Alright gammyhand. You have been around here a while. I'll straight shoot with you:

The Poofyhairguy guide to get things to work.

The plan:

Take you webcam. Throw it away or sell it on ebay. Buy a new webcam that is easier to get to work:

[http://www.linux.com/howtos/Webcam-HOWTO/devices.shtml](http://www.linux.com/howtos/Webcam-HOWTO/devices.shtml)

This plan is my favorite way (and the easiest way) to get hardware like webcams, wireless cards, or whatever else to work with Linux. I call the cost of the new hardware "the real price of Linux."

---

### Post by gammyhand on 2005-07-18
I see your point. I think I will have to follow your plan.

Any thoughts on why GAIM has resolutely refused to work since I installed aMSN?

---

### Post by gammyhand on 2005-07-18
[QUOTE=gammyhand]I see your point. I think I will have to follow your plan.

Any thoughts on why GAIM has resolutely refused to work since I installed aMSN?[/QUOTE]
 And if I buy a new webcam what the hell do I use for talking to people on IM apart from gnomemeeting.

---

### Post by gammyhand on 2005-07-18
[QUOTE=gammyhand]And if I buy a new webcam what the hell do I use for talking to people on IM apart from gnomemeeting.[/QUOTE]
 I found the driver CD for windows and this is the camera: 

[http://www.dynamode.net/cameras/M6215.htm](http://www.dynamode.net/cameras/M6215.htm)

Anyone got one working?

---

### Post by polo_step on 2005-07-19
[QUOTE=poofyhairguy]
Take you webcam. Throw it away or sell it on ebay. Buy a new webcam that is easier to get to work:

[http://www.linux.com/howtos/Webcam-HOWTO/devices.shtml](http://www.linux.com/howtos/Webcam-HOWTO/devices.shtml)
[/QUOTE]
In fairness, my webcam is on that list and has nominally been supported for a *long* time, and I can't get it to work anywhere near properly, if at all.

Being on that list is no guarantee that the device will work.

---

### Post by poofyhairguy on 2005-07-19
[QUOTE=gammyhand]And if I buy a new webcam what the hell do I use for talking to people on IM apart from gnomemeeting.[/QUOTE]

Amsn works:

[http://scapor.webpal.info/CAMS.png](http://scapor.webpal.info/CAMS.png)

---

### Post by az on 2005-07-19
[QUOTE=gammyhand]I found the driver CD for windows and this is the camera: 

[http://www.dynamode.net/cameras/M6215.htm](http://www.dynamode.net/cameras/M6215.htm)

Anyone got one working?[/QUOTE]


You cannot tell from that descrition.  Look in the .inf file for the Window's camera driver.   See if you can tell the chipset...

---

### Post by poofyhairguy on 2005-07-19
I asked the question for you:

[http://www.ubuntuforums.org/showthread.php?p=262419#post262419](http://www.ubuntuforums.org/showthread.php?p=262419#post262419)

Please wait for the answer.

---

### Post by lol on 2005-07-19
[QUOTE=gammyhand]And if I buy a new webcam what the hell do I use for talking to people on IM apart from gnomemeeting.[/QUOTE]

MSN and... Windows!

There is currently no IM client on linux with a good video support. You can try this [http://gaim-vv.sourceforge.net/](http://gaim-vv.sourceforge.net/) if you are really desperate but there is only a limited support for yahoo.

It's a pity, but this is the one thing where Linux sucks. The best workaround around this is to pretend you don't have a webcam to begin with :(

---

### Post by poofyhairguy on 2005-07-19
[QUOTE=lol]MSN and... Windows!
[/QUOTE]

Good idea. VMware might do the trick.

---

### Post by gammyhand on 2005-07-20
[QUOTE=azz]You cannot tell from that descrition.  Look in the .inf file for the Window's camera driver.   See if you can tell the chipset...[/QUOTE]
Ok. I managed to get the inf files but I can't tell...I have attached them hoping someone can point me in the right direction :)

---

### Post by az on 2005-07-20
SN9C10x

[http://www.linux-projects.org/modules/mydownloads/](http://www.linux-projects.org/modules/mydownloads/)

I do not know if that is the project homepage.  Check out this:

[http://www.linux-projects.org/modules/mydownloads/visit.php?cid=2&lid=31](http://www.linux-projects.org/modules/mydownloads/visit.php?cid=2&lid=31)

"Stable. Video4Linux2 driver for SN9C10x PC Camera Controllers connected to various image sensors.
THIS VERSION IS OBSOLETE FROM LINUX 2.6.12 ON: USE EITHER THE VERSION IN THE KERNEL (WITHOUT SUPPORT FOR SN9C103) OR THE BINARY-ONLY VERSION (WHICH HAS SUPPORT FOR SN9C103 AS WELL).
"

Perhaps Breezy will have a 2.6.12 kernel?

Anyway, the driver seems very stable and it is GPL...

Good!

Check out the tarball for a README as to how to install it...

---

### Post by gammyhand on 2005-07-20
[QUOTE=azz]SN9C10x

[http://www.linux-projects.org/modules/mydownloads/](http://www.linux-projects.org/modules/mydownloads/)

I do not know if that is the project homepage.  Check out this:

[http://www.linux-projects.org/modules/mydownloads/visit.php?cid=2&lid=31](http://www.linux-projects.org/modules/mydownloads/visit.php?cid=2&lid=31)

"Stable. Video4Linux2 driver for SN9C10x PC Camera Controllers connected to various image sensors.
THIS VERSION IS OBSOLETE FROM LINUX 2.6.12 ON: USE EITHER THE VERSION IN THE KERNEL (WITHOUT SUPPORT FOR SN9C103) OR THE BINARY-ONLY VERSION (WHICH HAS SUPPORT FOR SN9C103 AS WELL).
"

Perhaps Breezy will have a 2.6.12 kernel?

Anyway, the driver seems very stable and it is GPL...

Good!

Check out the tarball for a README as to how to install it...[/QUOTE]
 Thanks :) I am just about to re-install so I will have a go then.

I can't risk installing aMSN again. I know everyone says it's a GAIM bug, but absolutely nothing changed apart from installing that (which crashed badly) and GAIM not working. 

I must get some webcam software.

---

### Post by gammyhand on 2005-07-21
[QUOTE=gammyhand]Thanks :) I am just about to re-install so I will have a go then.

I can't risk installing aMSN again. I know everyone says it's a GAIM bug, but absolutely nothing changed apart from installing that (which crashed badly) and GAIM not working. 

I must get some webcam software.[/QUOTE]
 OK I re-installed and now when I plug in my webcam it is listed (with lsusb) as: Bus 001 Device 005: ID 0c45:602a Microdia Meade ETX-105EC Camera

However I still can't get it to do anything, a video chat website I tried said "no camera attached to your system"....weird??

---

### Post by az on 2005-07-21
What do you mean?  Did you install that driver?  Do you have v4l enabled in your X configuration?

---

### Post by gammyhand on 2005-07-21
[QUOTE=azz]What do you mean?  Did you install that driver?  Do you have v4l enabled in your X configuration?[/QUOTE]
 what is v4l? And I didn't install anything. It auto-detected that as the camera when I reformatted last night. How do I check for v4l in X configuration? I presume it is somewhere in xorg.conf?

---

### Post by lotusleaf on 2005-07-21
[QUOTE=gammyhand]what is v4l?[/QUOTE]

Many related links for you here:

[http://www.exploits.org/v4l/](http://www.exploits.org/v4l/)

---

### Post by polo_step on 2005-07-21
[QUOTE=lotusleaf]Many related links for you here:[/QUOTE]
I've been following this thread with some interest as I'm trying to get a functional webcam going as well.

After checking that link, I did some chasing around and discovered that a webcam that I had never been able to use (because the company whose name was on it went out of business before releasing XP drivers) may in fact be supported in Linux.

It's apparently a rebadged FlyVideo LR51 PCI capture card with the Conexant Bt879KHF chip. A Sanyo webcam plugs into it. According to some of these links, this is a supported device in the Linux kernel.

OK...so, I powered down the box and installed the PCI card and started up. I can't boot because the Hotplug system hangs during the boot sequence with the card in there. I let it sit there for a couple of minutes with no further progress so I powered down.  Same thing happened on the second try.  Pulled the card and the system booted fine again.

Any suggestion on this?

As always, thanks for any help.

---

### Post by amex on 2005-11-11
After a lot of searching, I found that if you are using a camera that uses the sn9c10x chipset (like Genius VideoCam NB, Sonix and some Dlink cameras) it is possible to make it work with gnomemeeting.

The problem with this cameras (actualy, the problem is the chip) is that it only work with v4l2 (VideoForLinux2) but almost all aplications for webcans in Linux only suport v4l (the first version).

So, if you are using a kernel >= 2.6.12 you already have a module that works fine with this cameras, the problem is that the applications does not. To see if you have the module run "lsmod | grep sn9c102" with you camera conected.

If yes, you can test it with a simple program from linux-projects that support v4l2: [http://www.linux-projects.org/modules/mydownloads/visit.php?cid=5&lid=35]("http://www.linux-projects.org/modules/mydownloads/visit.php?cid=5&lid=35")

Also, I found that there is a plugin to make gnomemeeting suport v4l2, so you can use it until other applications do not suport v4l2. To make it work do the following:

1.- Install libpt-plugins-v4l2 this way: "apt-get install libpt-plugins-v4l2" (maybe it is already installed).
2.- Open GnomeMeeting. It should still give you the error "Unable to connect to /dev/video0" or something like this, but don't care about it.
3.- Click on "Edit", "Preferences", "Video Devices"
4.- Change "Video Plugin" from v4l to v4l2.
(maybe the names here are different because I use Ubuntu in Brazilian Portuguese and I just try to translate the names).

It should work (at least it works here).

I hope it can help someone.

---

### Post by Wally68 on 2006-07-26
> The Poofyhairguy guide to get things to work.

The plan:

Take you webcam. Throw it away or sell it on ebay. Buy a new webcam that is easier to get to work:

[http://www.linux.com/howtos/Webcam-HOWTO/devices.shtml](http://www.linux.com/howtos/Webcam-HOWTO/devices.shtml)

This plan is my favorite way (and the easiest way) to get hardware like webcams, wireless cards, or whatever else to work with Linux. I call the cost of the new hardware "the real price of Linux."

I should have known better than to not take poofyhairguy seriously. I just wasted four days trying to get a Vivitar Vivicam 3340 to work in webcam mode. I learned lots in the process of almost getting the camera to work, the most important being:

**Always do what poofyhairguy said.**

---

### Post by fakie_flip on 2006-08-13
Is it possible to use windows xp drivers on Linux for webcams, just like a wireless network adapter can use windows drivers on linux with ndswrapper? I have a webcam that seems impossible on Ubuntu. I have tried everything that can be imagined.

---

