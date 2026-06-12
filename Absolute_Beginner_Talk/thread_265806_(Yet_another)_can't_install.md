---
title: "(Yet another) can't install"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by Jimbooo on 2006-09-26
Hi guys, first i'd like to quickly say thanks for everyone who posts on these forums to help the new guys out! It's great to see a community doing this kind of thing.

I'm totally new to the Linux O/S and I recently got a hold of a x64 Ubuntu cd which I have just tried to run on my computer. I boot from the cd and set my resolution and everything, then choose start.

Now the screen indicates everything has loaded properly yet I get the "dos like screen" and I have an error straight away saying something about my graphics card and would I like to find out what the problem is myself. I can type yes and then a load of y's start scrolling down the right side of the screen. There's nothing I can do about this except press alt and F4 to get back to a plain black screen command prompt.

Now i've tried typing in:

live
boot: live
live boot

loads of different combinations and I can't seem to get anything to run. I've also tried sh but I just can't do anything. I know this is really simple for you people most likely, but I would appreciate any help you can throw this way!:-k

---

### Post by Marsolin on 2006-09-26
It sounds like your graphics system isn't being recognized correctly. What hardware are you running on?

---

### Post by pay on 2006-09-26
> I'm totally new to the Linux O/S and I recently got a hold of a x64 Ubuntu cd which I have just tried to run on my computer.

The 64bit version of Ubuntu isn't the easiest to use for the beginner as alot of commercial software doesn't have a 64bit version. I would recommend to use the 32bit version until you get used to things.

---

### Post by Bachstelze on 2006-09-26
Hi and welcome to Ubuntu :)

Maybe a silly question but you say youre using a 64 bits CD, is your CPU 64 bits capable ?

---

### Post by pay on 2006-09-26
Try booting in safe graphics mode or download the Alternate install cd so you can install it in text mode.

---

### Post by pay on 2006-09-26
> **HymnToLife said:**
> Hi and welcome to Ubuntu :)

Maybe a silly question but you say youre using a 64 bits CD, is your CPU 64 bits capable ?

The cd wouldn't boot at all if that was the case. (I've done it by accident by not looking at the cd and putting it in the drive)

---

### Post by Jimbooo on 2006-09-26
Yes i'm 64 bit enabled! ;) 

My hardware is good enough to run vista at full power so you know it should be fine with linux...

Oh and my graphics card is a Geforce 7900 GT if that helps?

Also I just remembered I was asked if I wanted to "diagnose the problem" when I had the graphics error..

And last (not least) thanks for the warm welcome! Can't wait to get more involved in the community.

<EDIT> and i've tried safe graphics mode.. same problem ](*,)

---

### Post by pay on 2006-09-26
> **Jimbooo said:**
> 
Also I just remembered I was asked if I wanted to "diagnose the problem" when I had the graphics error..

It's not detecting your graphics card. Boot it in safe graphics or use the Alternate install cd.

---

### Post by commodore on 2006-09-26
I'm not saying anything useful now but there is no "the Linux OS". Linux is the kernel (the core of the operating system) and Ubuntu is an OS that uses the Linux kernel.

---

### Post by Jimbooo on 2006-09-26
Thanks for that Comm.. great to see there are still critical people out there! :p Oh and i'll just keep calling Linux an operating system, i'll survive! ](*,) 

Ok everyone else I tried tried loading on x86 on the lower graphical setting thing and I got the same error..

> "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

I can choose yes or no but I get onto the command prompt again and can't log onto anything. :(

---

### Post by Jimbooo on 2006-09-26
Any help anyone please?:-k

---

### Post by pay on 2006-09-26
Is that what it is doing in safe graphics mode aswell? You can try the alternate install found here [http://ftp.funet.fi/pub/Linux/INSTALL/Ubuntu/releases/dapper/ubuntu-6.06.1-alternate-i386.iso.torrent](http://ftp.funet.fi/pub/Linux/INSTALL/Ubuntu/releases/dapper/ubuntu-6.06.1-alternate-i386.iso.torrent)

---

### Post by Jimbooo on 2006-09-27
Okay I **removed my graphics card **(Geforce 7600 GT) and ran it off my **onboard** Geforce 6100.. and the installation worked. I got it onto my computer (thanks for all your comments to help me out)..

Now here's the problem, _I can't get it to find my modem_! I had a friend run SLAX Linux live-cd on my computer once and he couldn't get the modem working.. I can't even install the drivers for it using my cd (and I shouldn't need to because the *lights on my modem are green*, *not red like normally when drivers aren't installed*).

I want to actually start using the OS but I can't yet because I can't get even my basic peripherals working. Anyone help?

**Also, is there any way that I can get Ubuntu Linux to work with my graphics card?**

---

### Post by gn2 on 2006-09-27
I would suggest investing in a combined modem router firewall device something like a Netgear DG834G?
They are not expensive these days and your modem problem will cease to exist.
Perhaps sell old modem it on eBay to help fund the router purchase?

---

### Post by bodhi.zazen on 2006-09-27
> **Jimbooo said:**
> **Also, is there any way that I can get Ubuntu Linux to work with my graphics card?**

Yes. Install the nvidia drivers:

[[color=blue]How to install Nvidia drivers[/color]](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Use method 2.

---

### Post by Jimbooo on 2006-09-28
Thanks for that! :D One small problem though, when it says the packages to download the links do not work. Can you link elsewhare please I can't seem to find them on google (because I don't know* exactly* what i'm searching for lol..

> 2) Download this package from another computer (in which you have an internet connection): 

Use this package if you run Ubuntu 32bit: 

Nvidia_package_32 :confused: 

OR this package if you run Ubuntu 64bit: 

Nvidia_package_64 :confused: 

Then move the package to your computer with Ubuntu (use a USB pen for example): Double click on the .deb file and install it. 


---

