---
title: "Working with KVM and nVidia (two separate issues)"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Frankenbean on 2007-06-27
Hi everyone.  I posted here because I am a complete newbie to Ubuntu.  I've toyed with linux a few times in the past, and did some Irix in college, but that was a long long time ago.

My first issue is with my nVidia Geforce 7600 GS.  I've installed it several different ways, and X always fails to start.  I've used the 'Restricted Drivers' method, I've used Envy, and I've tried to manually go in and edit my xorg.conf.  No matter what, when I try to use an nVidia driver, X fails to start, and I have to go back to Device=vesa in my xorg.conf.  Does anyone have any further tips?

My second issue is with KVM.  I have two virtual machines installed (Win Server 2003 and Win XP).  I want to network them so that they can ping each other, and I would like to be able to let the server get to the internet.  Then the ultimate goal is to use the server virtual machine as the XP machine's default gateway so I can install and test SUS.  

I've looked at [https://help.ubuntu.com/community/KVM#head-db5235851cc1b9c712f99a074f02c91e8590c880]("https://help.ubuntu.com/community/KVM#head-db5235851cc1b9c712f99a074f02c91e8590c880")
And quite frankly it's beyond me.  Are there any other how to's that anyone has used?

Many Thanks
-john

---

### Post by PCFascist on 2007-06-27
> **Frankenbean said:**
> Hi everyone.  I posted here because I am a complete newbie to Ubuntu.  I've toyed with linux a few times in the past, and did some Irix in college, but that was a long long time ago.

My first issue is with my nVidia Geforce 7600 GS.  I've installed it several different ways, and X always fails to start.  I've used the 'Restricted Drivers' method, I've used Envy, and I've tried to manually go in and edit my xorg.conf.  No matter what, when I try to use an nVidia driver, X fails to start, and I have to go back to Device=vesa in my xorg.conf.  Does anyone have any further tips?


The nVidia restricted driver is unsupported so I don't think you'll have any help with it here... but if you have a GOAL on what you'd like to do with your xorgconf you should restate it because it isn't clear what we are helping you with on this issue. Please also let us know what display you have connected to the box.

---

### Post by bodhi.zazen on 2007-06-27
> **Frankenbean said:**
> Hi everyone.  I posted here because I am a complete newbie to Ubuntu.  I've toyed with linux a few times in the past, and did some Irix in college, but that was a long long time ago.

My first issue is with my nVidia Geforce 7600 GS.  I've installed it several different ways, and X always fails to start.  I've used the 'Restricted Drivers' method, I've used Envy, and I've tried to manually go in and edit my xorg.conf.  No matter what, when I try to use an nVidia driver, X fails to start, and I have to go back to Device=vesa in my xorg.conf.  Does anyone have any further tips?

What is the error message with the nvidia card ?

Try this :

[http://ubuntuforums.org/showpost.php?p=2897131&postcount=6](http://ubuntuforums.org/showpost.php?p=2897131&postcount=6)

With KVM, I agree networking is complex ;)

In that link, in the "Advanced Networking" section, enter those commands to configure your network.

If it works, add those commands to /etc/rc.local

Also, see this wiki page :

[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

^^ Look at the "TAP network" section

---

