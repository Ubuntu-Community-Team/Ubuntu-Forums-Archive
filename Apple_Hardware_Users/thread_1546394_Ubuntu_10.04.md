---
title: "Ubuntu 10.04"
date: 2010-08-05
forum: Apple Hardware Users
---

### Post by OpenOS on 2010-08-05
I have just recently brought a macintosh for £999 and i wanted to dual boot mac os 10 with ubuntu so far i have failed does anyone have the solution. (i dont want to use bootcamp or parrells since it formatted the hard disk the last time)

Thanks

---

### Post by decidedlyno9 on 2010-08-05
How about Vmware Fusion or VirtualBox?


I run Fusion 3.1.0 with XP and Ubuntu 10.04 and it works perfectly on 10.6.4. 

While, I have read that VirtualBox is becoming a contender in this market and I think it is free ([http://www.virtualbox.org/](http://www.virtualbox.org/)).

---

### Post by OpenOS on 2010-08-05
ive allready done that but i want it as a partition to dual boot normally without virtual machines

---

### Post by decidedlyno9 on 2010-08-05
Hmm... You’re in quite a predicament then, all the best though.

---

### Post by amd-64 on 2010-08-05
You need to give more information so someone could help. Was there a specific error message. Are you following the installation guide for your hardware from here
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by OpenOS on 2010-08-05
its not an error message before i boot into mac os x i hold down c for i beileve to be a bootable drive option but correct me if im wrong it boots the ubuntu cd i choose the english language then i choose the install ubuntu option after that its just a black screen ive even left it for 5 hours and still came back to a black screen. Also its an iMac11, 2

---

### Post by dave-knuckle on 2010-08-06
I hope this tutorial helps

[http://www.dreamincode.net/forums/topic/44217-dual-boot-linux-on-a-macbook/](http://www.dreamincode.net/forums/topic/44217-dual-boot-linux-on-a-macbook/)

best of luck-----------------------D-K

---

### Post by OpenOS on 2010-08-06
Thanks for the help guys but what would be perfect if canonical made a deal with apple to make a continuous dual boot capabillity.

---

### Post by pyedog on 2010-08-26
I am having the same problem with this machine, which is a pain as I am missing using Ubuntu. I managed to get Fedora to boot and install but after that there were problems booting into the installed system.

Fedora would be better than this awful OSX system, Ubuntu would be ideal. I'll file a bug report for it later if I get time, hopefully try to get it fixed for Maverick.

To the OP: I've not had chance to try it yet, but you could try Alt+F1 to drop to a console and see if that displays correctly. I think the problem is something to do with the graphics card, since the screen doesn't go black until after the splash screen and it would appear the machine is functioning apart from the display. In fact, I'm gonna try that now.

---

### Post by dngfng on 2010-08-27
Best option is to handle Multi-Boot via rEFIt worked great for me.

Just follow this tutorial, I know its for triple boot system but it is easy enough to ignore the windows part if you only want to have OS X / Linux dual boot.

[http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required](http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required)

---

### Post by pyedog on 2010-08-27
Ah, I misunderstood the problem. Yes, rEFIt is the best solution for dual-booting with Linux. There are many tutorials out there.

You might find though, that if your Mac is one of the ones with the  ATI Radeon graphics cards that the live CD will fail to load and boot into a black screen. I was pulling my hair out all last night trying to boot the Ubuntu CD but ended up installing Linux Mint 9, since the live CD allowed me to run in 'compatibility mode'.

Without the ATI problem though, installing Ubuntu using rEFIt should be smooth and painless.

Also, you might get more replies to your post if you use a more descriptive title than 'Ubuntu 10.04'. :D

---

### Post by dngfng on 2010-08-27
> **pyedog said:**
> Ah, I misunderstood the problem. Yes, rEFIt is the best solution for dual-booting with Linux. There are many tutorials out there.

You might find though, that if your Mac is one of the ones with the  ATI Radeon graphics cards that the live CD will fail to load and boot into a black screen. I was pulling my hair out all last night trying to boot the Ubuntu CD but ended up installing Linux Mint 9, since the live CD allowed me to run in 'compatibility mode'.

Without the ATI problem though, installing Ubuntu using rEFIt should be smooth and painless.

Also, you might get more replies to your post if you use a more descriptive title than 'Ubuntu 10.04'. :D

In that case I am real happy that mine has got an Nvidia card. :p

Totally agree with you on the subject matter - a more descriptive title would have gotten better responses.

---

