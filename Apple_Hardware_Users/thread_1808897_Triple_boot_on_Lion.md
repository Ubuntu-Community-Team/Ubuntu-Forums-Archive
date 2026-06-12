---
title: "Triple boot on Lion"
date: 2011-07-20
forum: Apple Hardware Users
---

### Post by daryllee on 2011-07-20
I am a week or so from receiving a new Macbook for work.  I do multi-OS development, supporting mainly  Windows and Linux, and preferring Apple hardware and UI for a multitude of reasons.  I need to be able to run each OS (Lion, Windows 7, Ubuntu) and am looking for the best approach.  In a perfect world, the three would be "peers", letting me choose which one at boot time, and with each having read/write access to a common directory structure for such data as documents, source code repository, and mail.  

Bootcamp does not appear to recognize Linux.  "rEFIt" looked like a good solution, but I have read on several forums that Lion has broken compatibility with rEFIt.  I would be willing to accept a Wubi-type installation if necessary.  Is it possible to configure a Wubi-based system so that all OSes can share a common directory tree?  For instance, I'd like something like a /common directory tree, where I could locate a single source code repository tree and a single Thunderbird email profile.

Any advice, especially from those with experience in multi-booting, is appreciated.

---

### Post by jerrycal on 2011-07-21
> **daryllee said:**
> I am a week or so from receiving a new Macbook for work.  I do multi-OS development, supporting mainly  Windows and Linux, and preferring Apple hardware and UI for a multitude of reasons.  I need to be able to run each OS (Lion, Windows 7, Ubuntu) and am looking for the best approach.  In a perfect world, the three would be "peers", letting me choose which one at boot time, and with each having read/write access to a common directory structure for such data as documents, source code repository, and mail.  

Bootcamp does not appear to recognize Linux.  "rEFIt" looked like a good solution, but I have read on several forums that Lion has broken compatibility with rEFIt.  I would be willing to accept a Wubi-type installation if necessary.  Is it possible to configure a Wubi-based system so that all OSes can share a common directory tree?  For instance, I'd like something like a /common directory tree, where I could locate a single source code repository tree and a single Thunderbird email profile.

Any advice, especially from those with experience in multi-booting, is appreciated.


I just installed Lion and rEFIt works fine, but even if it didn't, all you have to do is hold "Option" key to select which OS to boot to. 
When you get your Mac, you'll have to see which version you have and then use this Community Documentation: [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) 
P.S. Bootcamp will create partition for you (it will call it "Windows") but you can use disk utility in Mac OSX or gparted from Ubuntu Live CD to partition your drive.

---

### Post by daryllee on 2011-07-21
Thanks!  I'll report back on my results.  Any guidance on how to arrange for the common data area?  My instinct is to create a separate partition, formatted ext3.

---

### Post by 2F4U on 2011-07-21
Have you ever thought about using virtual machines instead of physically installing three operating systems on one machine? I have no idea on what development work you do and a VM is certainly not the right choice for e.g. driver development. However, if you choose to use VM's it will certainly be easier than triple booting and you can even run more than one OS in parallel. There are several VM vendors available for a Mac, for example VirtualBox, Parallels and VMWare.

---

### Post by daryllee on 2011-07-21
> **2F4U said:**
> Have you ever thought about using virtual machines instead of physically installing three operating systems on one machine? I have no idea on what development work you do and a VM is certainly not the right choice for e.g. driver development. However, if you choose to use VM's it will certainly be easier than triple booting and you can even run more than one OS in parallel. There are several VM vendors available for a Mac, for example VirtualBox, Parallels and VMWare.

And therein is the problem.  I do fairly high-speed robotics control apps, with 1msec servo loop times, and OpenGL graphics and sound effects on top of that.  VMs won't cut it for me.  I DO expect to use VMs for most of the edit/build/document effort, but when it comes test time, only a native OS will do.

---

### Post by jerrycal on 2011-07-21
> **daryllee said:**
> Thanks!  I'll report back on my results.  Any guidance on how to arrange for the common data area?  My instinct is to create a separate partition, formatted ext3.


Here is pretty good guide on creating separate home partition:
[http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems](http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems)

---

### Post by daryllee on 2011-07-21
> **jerrycal said:**
> Here is pretty good guide on creating separate home partition:
[http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems](http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems)

Thanks.  The "Part Two" approach looks like just what I want.  Now to just take delivery of the new hardware...

---

### Post by daryllee on 2011-08-02
Well, to my surprise, my MacBook pro arrived with Snow Leopard on it.  I now have triple-boot working following the LifeHacker instructions, basically.  There are only two things I need to add.  

I used ext3 for the Linux partition, installed Paragon extFS ($39.95) on OS X and extFsd ([http://sourceforge.net/projects/ext2fsd/;](http://sourceforge.net/projects/ext2fsd/;) Open Source) for Windows.  My shared data is in /Common on the Linux partition, and seems to work fine (so far) without any issues related to users (same user name on all OSes).

I haven't been through the full driver setup on Ubuntu yet, but apparently I have no way to get WiFi working.  My workaround is to use the Personal Hotspot feature of my iPhone.  I'd like to find a proper way to get Wifi working, and if I do I'll post it here.

---

### Post by blane2 on 2011-08-02
the new macbooks don't run ubuntu very well yet.

*edit

I see you got SL and it's set up minus wifi.. keep us informed

---

### Post by tgalati4 on 2011-08-02
Also understand that there are some proprietary Intel power-saving features that only OSX and Win7 can access, so running Ubuntu can cause your machine to overheat and destroy itself.  Search the web, there have been stories of Apple denying warranty claims due to running a non-approved operating system.

---

### Post by jerrycal on 2011-08-02
To get wifi working you have to go to: Additional Drivers, and then activate Broadcom STA driver. Also, there will be nVidia driver to activate as well. As far as Macs running hot and other features like turning on keyboard light refer to this: [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

---

### Post by daryllee on 2011-08-02
By "Additional Drivers", I'm guessing you mean that I should find a tab or button or something under Administration->Hardware Drivers.  But that dialog box is empty, except for a line at the top saying "No proprietary drivers are in use on this system."  Am I looking in the wrong place?  Or is there some mantra for populating that dialog with something interesting?  Also, I've set "Software Sources" to include everything but source code under the Ubuntu Software tab and "archive.canonical.com/ubuntu lucid partner" and "ppa.launchpad.net/mozillateam/firefox-stable/ubuntu lucid main" under the Other Software tab.

---

### Post by jerrycal on 2011-08-03
> **daryllee said:**
> By "Additional Drivers", I'm guessing you mean that I should find a tab or button or something under Administration->Hardware Drivers.  But that dialog box is empty, except for a line at the top saying "No proprietary drivers are in use on this system."  Am I looking in the wrong place?  Or is there some mantra for populating that dialog with something interesting?  Also, I've set "Software Sources" to include everything but source code under the Ubuntu Software tab and "archive.canonical.com/ubuntu lucid partner" and "ppa.launchpad.net/mozillateam/firefox-stable/ubuntu lucid main" under the Other Software tab.


Yes, that's what I meant - the Hardware drivers under Administration. Did you do "update" after setting the SW sources? Also, there may be "Proprietary drivers for devices (restricted) in the source list. If you want to stick with Lucid for the time being, and not upgrade to Maverick or Natty, I'd burn "Natty CD" and boot from that and see if it brings up dialog that Additional drivers are available. Otherwise you may have to start a new thread for that issue.

---

### Post by daryllee on 2011-08-03
> **jerrycal said:**
> Yes, that's what I meant - the Hardware drivers under Administration. Did you do "update" after setting the SW sources? Also, there may be "Proprietary drivers for devices (restricted) in the source list. If you want to stick with Lucid for the time being, and not upgrade to Maverick or Natty, I'd burn "Natty CD" and boot from that and see if it brings up dialog that Additional drivers are available. Otherwise you may have to start a new thread for that issue.

I think I need to stick with Lucid because that's what my customer requires.  I'll have a look at Natty and see what I learn.  Thanks in advance.

---

