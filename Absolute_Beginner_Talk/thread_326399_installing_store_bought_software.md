---
title: "installing store bought software"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by beanermw on 2006-12-27
](*,)  I was able to get a computer for my daughter from the local school district for cheap, but they had to uninstall windows and install Ubuntu as the OS.  The problem is that we are unfamiliar with Ubuntu.  I got the disc to install edubuntu since the computer is for a 7 y.o. and there is more educational stuff included with it.  Our problem is that she has cd roms that we have used with windows os, but we cannot figure out how to install them on the computer with edubuntu.  I have searched some of the listings on this site with no success.  HELP!!!  She really enjoys the games on cd rom, but can only play them on my computer.

---

### Post by bastiegast on 2006-12-27
I'm afraid you will have to find other software for your daughter to play with. Windows software generally doesn't work with ubuntu (linux). There are projects such as [wine]("http://www.winehq.com/") that try to address this problem. With wine you can run windows programs in linux although it usually is a pain to get things working.

You should have a look at available alternative software for ubuntu. Open the applications menu and hit "Install/Remove" look in Games or Education, there's lots of free software there.

---

### Post by stalker145 on 2006-12-27
In order to use Windows applications you will need to install Wine. There is a fine [HowTo here]("https://help.ubuntu.com/community/Wine") that should get you going. The only thing is that Wine is not 100% guaranteed to work with your applications. 

There is a pretty good list of compatable applications on the [Wine web site]("http://appdb.winehq.org/") that will tell you your chances of success. If it's not there, it might still work, so why not give it a go anyway?

Good luck

---

### Post by spockrock on 2006-12-27
well for starters in general windows software wont run on gnu/linux.  There are multiple solutions though.

1.  Dual Boot, you can install windows on the machine and dual boot edubuntu and windows.  You may have to create a partition for it to install, however if you install windows after edubuntu then you will have to re-install grub.  Don't worry its easier then it sounds......

2. Run windows in a virtual environment.  You can use qemu, vmware player/server to run windows inside of edubuntu.  Windows will be in its own window in edubuntu and then you can run the programs that way.

3. WINE, wine lets you run windows apps in gnu/linux, there are many guides here to help you, on how to install and setup, this runs windows applications inside of gnu/linux, that being said, its not 100%, 

From what I understand, I think what you originally want is wine, but again, wine isn't perfect it can't run everything and functionality is still missing.

---

### Post by gn2 on 2006-12-27
Another simpler solution to your specific problem is to get a copy of Windows 2000 Professional cheap from eBay.

---

### Post by beanermw on 2006-12-27
> **stalker145 said:**
> In order to use Windows applications you will need to install Wine. There is a fine [HowTo here]("https://help.ubuntu.com/community/Wine") that should get you going. The only thing is that Wine is not 100% guaranteed to work with your applications. 

There is a pretty good list of compatable applications on the [Wine web site]("http://appdb.winehq.org/") that will tell you your chances of success. If it's not there, it might still work, so why not give it a go anyway?

Good luck



Do I have to be connected to the internet to install wine?  I have to use a cd to log her on with our dsl the first time.  :???:

---

### Post by az on 2006-12-27
> **beanermw said:**
> Do I have to be connected to the internet to install wine?  I have to use a cd to log her on with our dsl the first time.  :???:

If a computer is connected to a net connection that uses pppoe (a small number of adsl connections), you need to open a terminal and run

sudo pppoeconf

and answer the prompts (username password)  anything you don't know, just take the default.  If this computer is connected to adsl through a router, the router takes care of that and your Ubuntu computer will be connected at boot time, automatically.

You will need to enable the Universe repository to install wine:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Perhaps you will also find this documentation helpful:
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

I really doubt there are many of those kinds of games that run on wine.  They all seem to use microsoft's proprietary 3D graphics infrastructure (DirectX) - wine does not do that.

---

### Post by wpshooter on 2006-12-27
Beanermw:

I don't exactly understand the second sentence of your reply above.

Do you have the Ubuntu or Edubuntu O/Ss one or the other installed on the hard drive of your daughter's computer ?

I really agree with AZZ.  I think you are probably going to be very disappointed if you are going to attempt to run Windows based software using WINE or other similar programs.

Probably the best you are going to be able to do, is to find and convince her to start using Linux based games.

Good luck.

---

### Post by beanermw on 2006-12-27
I originally had ubuntu, but when I saw edubutu on the website, I ordered the cd for it and now she has edubuntu on the computer.

---

### Post by wpshooter on 2006-12-27
Maybe we will get to the point in several years where some of the major application software developers start to offer there programs in NATIVE Linux offerings but I would think that this would probably be most all other types of applications first and then down the road MAYBE games might following but I wouldn't want to hold my breath waiting for it to happen.

---

### Post by beanermw on 2006-12-27
> **azz said:**
> If a computer is connected to a net connection that uses pppoe (a small number of adsl connections), you need to open a terminal and run

sudo pppoeconf

and answer the prompts (username password)  anything you don't know, just take the default.  If this computer is connected to adsl through a router, the router takes care of that and your Ubuntu computer will be connected at boot time, automatically.

You will need to enable the Universe repository to install wine:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Perhaps you will also find this documentation helpful:
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

I really doubt there are many of those kinds of games that run on wine.  They all seem to use microsoft's proprietary 3D graphics infrastructure (DirectX) - wine does not do that.
I tried the "sudo pppoeconf" and it didn't work.  Any other suggestions?  After it tries to do a scan it brings a window up that says "sorry, I scanned 2 interfaces, but the Access Concentrator of your provider did not respond.  Please check your network and modem cables.  Another reason for the scan failure may also be another running pppoe process which controls the modem."  I checked my cables and even restarted my modem and tried again with no success.

---

