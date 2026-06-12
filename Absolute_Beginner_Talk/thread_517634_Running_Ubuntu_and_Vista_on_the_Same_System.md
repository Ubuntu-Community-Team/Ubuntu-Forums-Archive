---
title: "Running Ubuntu and Vista on the Same System?"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by T-Fox on 2007-08-04
Hi, I am brand new to Ubuntu, and to Linux in general. I am running from the boot CD, and so far am liking what I see. Although, there are some instances in which I would prefer to be able to book in windows too. So, is there any way to Partition the Hard Drive, and be able to choose between Ubuntu Linux and Windows Vista before startup?

Thank you so much.

~T-Fox.

---

### Post by overdrank on 2007-08-04
> **T-Fox said:**
> Hi, I am brand new to Ubuntu, and to Linux in general. I am running from the boot CD, and so far am liking what I see. Although, there are some instances in which I would prefer to be able to book in windows too. So, is there any way to Partition the Hard Drive, and be able to choose between Ubuntu Linux and Windows Vista before startup?

Thank you so much.

~T-Fox.

Hi here is some great info
[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)
Good luck and welcome!:)

---

### Post by Jimmyfj on 2007-08-04
Hi T-Fox and welcome to Ubuntu

Yes, there is a way - You could dual-boot the two. Just remember to defrag your Windows before you install Ubuntu. 

My first advice is for you to play around with the live Cd some more, just to get the feel of Ubuntu. This way you wont mess up the Windows install in case anything goes wrong.

---

### Post by T-Fox on 2007-08-04
> **Jimmyfj said:**
> Hi T-Fox and welcome to Ubuntu

Yes, there is a way - You could dual-boot the two. Just remember to defrag your Windows before you install Ubuntu. 

My first advice is for you to play around with the live Cd some more, just to get the feel of Ubuntu. This way you wont mess up the Windows install in case anything goes wrong.

Ok, I'll play around with it a little more before I Install. One Quick Question though. I wanted to test out my games in Ubuntu before I installed, so I tried World of Warcraft. When I found the folder and selected the Launcher, it gave me an Error stating:  "Cannot open /media/disk/Program Files/World of Warcraft/Launcher.exe: No application suitable for automatic installation is available for handling this kind of file."

Does anyone know what to do about this?

~T-Fox

---

### Post by Jimmyfj on 2007-08-04
To be able to play Windows based games in Ubuntu you need to use Wine. For that you need to install Ubuntu on your harddrive. Can't say if it works on Live Cd. But try and go to Applications/Add/Remove/Office and install wine from there. Can't guarantee that it'll work though. Never tried Wine that way.

Edit: Here's a link on WoW on Linux - I should run alright: 

[http://www.desktoplinux.com/news/NS4727367100.html](http://www.desktoplinux.com/news/NS4727367100.html)

Try this one too

[http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

---

### Post by belikralj on 2007-08-04
You can't run windows programs in Ubuntu, for that you will need to install wine and your games will probably run a little slower than they do in windows. It should be in the Synaptic and if not try here:

[http://www.winehq.org/](http://www.winehq.org/)

It appears I just repeated your words :)

---

### Post by MQMike on 2007-08-04
***   The definitive dual-booting guide: Linux, Vista and XP step-by-step
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)

Looks easy.  Best How-To I've seen on this as of today's date.

---

### Post by HermanAB on 2007-08-04
Linux plays nice in groups and if the install program detects a Windows partition, then it will arrange for a Windows entry in the boot loader.

However, virtualization tools have improved enormously in the past few years.  Therefore my favourite solution is to install VMware Server (Qemu or VirtualBox) and install Windows XP in that.  Then I can run Windows in a window, concurrently with any Linux applications.  This is much more convenient than dual booting where you end up wishing that you were running the other system.

Cheers,

Herman

---

