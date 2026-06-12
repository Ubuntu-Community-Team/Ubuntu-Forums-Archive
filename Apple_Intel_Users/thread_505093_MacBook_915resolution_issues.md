---
title: "MacBook 915resolution issues"
date: 2007-07-19
forum: Apple Intel Users
---

### Post by baxter86 on 2007-07-19
Hi everyone.

First, I just want to say I'm a complete newbie when it comes to Ubuntu, but I am trying to learn it through reading articles/posts/FAQs on the net. That being said, onto my problem(s):

I have a first gen MacBook Core Duo @ 2ghz w/ 1gb RAM. I've installed Ubuntu ver. 7.04 using Parallels (with 512mb allocated to Ubuntu) on OSX (latest build). Ubuntu loads nicely, I have working sound and internet. My problem lies in the graphics/video adapter. I'll admit that one of the main reasons I wanted to give Ubuntu a go was for the eye-candy it offers. However I have not been able to get that to work.

Here's what I've tried so far. From another post here, I've attempted to install the 915resolution drivers by typing the following

> sudo apt-get install 915resolution

I then noticed it downloading the packages. Great right? After shutting off Ubuntu (and stopping the VM in Parallels) I started everything back up again. 

I then tried to activate Desktop Effects: System-Prefrences-Desktop Effects. At this point I get a completely blank white screen. After waiting the 30 seconds my display returns and I exit the Desktop Effects screen. I go back to terminal to see if 915resolution has been installed (by repeating the previous command) and I receive the following information.

....915resolution is already the newest version...

Can anyone help me out here?  :confused:

FYI here's the link to a post made by someone on this website with regards to using 915resolution as the default driver for the Intel graphics chipset on the macbook:

[http://ubuntuforums.org/showthread.php?t=450534](http://ubuntuforums.org/showthread.php?t=450534)

---

### Post by cyberdork33 on 2007-07-19
Running Ubuntu in parallels is not running Ubuntu on your Mac, it is running Ubuntu in a Virtual Machine. This means that your REAL hardware is not the same hardware that is seen by your OS in parallels.

Also, As far as I know, parallels does not support 3D graphics for linux, and thus the effects will not work (and definitely not 915resolution as it is for your real hardware.)

---

### Post by baxter86 on 2007-07-19
Damn, I thought parallels supported OpenGL but VMware didn't.

So, in order for Ubuntu to work with Desktop Effects, Beryl etc, I'd have to install it as the main OS? Does this mean I won't be able to run OSX and Ubuntu simultaneously? If that's the case, would bootcamp work?

---

### Post by cyberdork33 on 2007-07-20
> **baxter86 said:**
> Damn, I thought parallels supported OpenGL but VMware didn't.

So, in order for Ubuntu to work with Desktop Effects, Beryl etc, I'd have to install it as the main OS? 
no
> Does this mean I won't be able to run OSX and Ubuntu simultaneously? If that's the case, would bootcamp work?

you can dual boot, yes. there are several guides in this forum as well as others. you can use bootcamp to resize your OSX partition and create a new one. then just boot the ubuntu cd and delete the windows partition, and install ubuntu in the free space. There are more thorough guides around...

---

### Post by rskjr on 2007-08-05
sudo apt-get install xserver-xorg-video-intel

I found that this worked.  I'm not sure why, but after I ran this, I had the correct resolutions displayed (I'm dual booting, not using Parallels.)

---

