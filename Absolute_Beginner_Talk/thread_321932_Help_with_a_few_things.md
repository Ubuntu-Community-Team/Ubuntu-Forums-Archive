---
title: "Help with a few things"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Genius314 on 2006-12-19
Ok, I am currently running Ubuntu and Win ME on the same system. Right now I'm using Windows, because I can't seem to figure out how to get on the internet in Ubuntu.

1. Is it possible to access my hard drive from Ubuntu? I can't find any of my files using Ubuntu. Also, can I access files that I make in Ubuntu when I'm using Windows?

2. Is it possible to get dual monitors working in Ubuntu? The second monitor works, just not in Ubuntu.

3. The highest resolution that's listed in Ubuntu is 1024x768. Is it possible to go any bigger? (right now I have 1280x1024 in Windows).

4. I have a Wacom Graphire 3 tablet. The mouse acts odd in Ubuntu. Basically, whenever I lift the mouse and place it back on the tablet, the cursor moves to that point on the screen. I know that there should be a way to switch between "pen" and "mouse" mode, yet I can't find it.

[COLOR="Silver"]5. I have a Belkin Router in another room, and I connect through a Belkin USB wireless card (or whatever it's called.) How do I set this up to be able to connect through the internet?[/COLOR]

And that's pretty much it for now.
Thanks.

---

### Post by lamego on 2006-12-19
> 1. Is it possible to access my hard drive from Ubuntu? I can't find any of my files using Ubuntu. Also, can I access files that I make in Ubuntu when I'm using Windows?
If you have chosen ext3 filesystems you can access them from windows with the following driver:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by bodhi.zazen on 2006-12-19
> **Genius314 said:**
> Ok, I am currently running Ubuntu and Win ME on the same system. Right now I'm using Windows, because I can't seem to figure out how to get on the internet in Ubuntu.

1. Is it possible to access my hard drive from Ubuntu? I can't find any of my files using Ubuntu. Also, can I access files that I make in Ubuntu when I'm using Windows?

Yes, no problem:

Mounting and permissions depends on the file system:

_Windows:_

For ntfs: [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)

for read-write ntfs use: [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g)

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).

 For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

For widows see: [http://www.fs-driver.org/](http://www.fs-driver.org/)

```
2. Is it possible to get dual monitors working in Ubuntu? The second monitor works, just not in Ubuntu.
```

Yes.

[How to dual monitor](http://www.ubuntuforums.org/showthread.php?t=240150)

Follow the links for twinview......

> ]3. The highest resolution that's listed in Ubuntu is 1024x768. Is it possible to go any bigger? (right now I have 1280x1024 in Windows).

Post xorg.conf (that's /etc/X11/xorg.conf to you !), monitor, and graphics card.

See also: [How to set your monitor resolution](http://www.ubuntuforums.org/showthread.php?&t=240150)

> 4. I have a Wacom Graphire 3 tablet. The mouse acts odd in Ubuntu. Basically, whenever I lift the mouse and place it back on the tablet, the cursor moves to that point on the screen. I know that there should be a way to switch between "pen" and "mouse" mode, yet I can't find it.

5. I have a Belkin Router in another room, and I connect through a Belkin USB wireless card (or whatever it's called.) How do I set this up to be able to connect through the internet?

And that's pretty much it for now.
Thanks.

Not sure on those last two :(

HTH

---

### Post by Jareth on 2006-12-19
Here's instructions I use for mounting win98 under linux

First off open a console >>>
 
cd /
 
sudo mkdir windows
 
sudo chmod 777 -R /windows
 
then >>>
 
sudo gedit /etc/fstab
 
then add this line at the end >>>
 
/dev/hda1  /windows   vfat   iocharset=utf8,umask=000   0       0
 
then press enter to the next line down
 
and save the file and reboot, you will then have your windows drive accessable and writeable
 
to get to it goto System > places > filesystem > windows

---

### Post by Genius314 on 2006-12-20
Ok, thanks for the help. Unfortunately, this isn't going to help me until I can get the internet working in Linux.
[COLOR="Silver"]I've followed instructions on how to install the Wireless Adapter using Ndiswrapper. Now it gave me instructions to go to System>Administrator>Networking, and click on the type of connection I want to use. Yet the only connection type I see is "modem." No "wireless" or anything like that. How do I get this to work?[/COLOR]
Also, does Ndiswrapper work for any type of Windows driver? Could I use it for my mouse, or flash drive? Or is it only for Network cards?

EDIT: Ok, never mind the grayed-out part. It appeared after a reboot (it was so obvious...). Now I just have to figure out how to configure it. I should be able to do this on my own.
EDIT2: YES!! It works. I'm now editing this post from Ubuntu. Now I don't have to keep shutting down and switching between Ubuntu and WinME.

---

### Post by bodhi.zazen on 2006-12-20
> **Genius314 said:**
> EDIT2: YES!! It works. I'm now editing this post from Ubuntu. Now I don't have to keep shutting down and switching between Ubuntu and WinME.

Can't quite follow, but:

[indent]Welcome to Ubuntu[/indent]

---

### Post by lyceum on 2006-12-20
> **Genius314 said:**
> Ok, I am currently running Ubuntu and Win ME on the same system. Right now I'm using Windows, because I can't seem to figure out how to get on the internet in Ubuntu

5. I have a Belkin Router in another room, and I connect through a Belkin USB wireless card (or whatever it's called.) How do I set this up to be able to connect through the internet?

And that's pretty much it for now.
Thanks.

#5 will need to be #1. 

What kind of belkin USB wireless router are you using? What is the modle #? Once you get that running, and connect to the net, you can move to the next steps.

---

### Post by Genius314 on 2006-12-20
> #5 will need to be #1.

What kind of belkin USB wireless router are you using? What is the modle #? Once you get that running, and connect to the net, you can move to the next steps.

I got it working. I don't need help now.

OK, I'm trying to get my second monitor to work, and I still need to get my resolution back up to 1280x1024. Is there an easier GUI way to do this, rather than editing a config file? I'm just getting a bit confused with all the tutorials. ](*,)

---

### Post by lyceum on 2006-12-20
> **Genius314 said:**
> I got it working. I don't need help now.

OK, I'm trying to get my second monitor to work, and I still need to get my resolution back up to 1280x1024. Is there an easier GUI way to do this, rather than editing a config file? I'm just getting a bit confused with all the tutorials. ](*,)

Cool. 

As for the monitors, I can help you once I get home, but that will not be for 6 hours. If you do not have it working by then, I'll post a fix, but I can tell you right now that it may not be very easy. I see a lot of people with this question on the forum. If their how to's don't help, I may not be able do much better.

---

### Post by macogw on 2006-12-20
Do you by any chance have an Intel graphics card?  If so, download the package 915resolution.

---

### Post by bodhi.zazen on 2006-12-20
> **Genius314 said:**
> I got it working. I don't need help now.

OK, I'm trying to get my second monitor to work, and I still need to get my resolution back up to 1280x1024. Is there an easier GUI way to do this, rather than editing a config file? I'm just getting a bit confused with all the tutorials. ](*,)

There is a gui that may help: [http://www.cyskat.de/dee/progxorg.htm](http://www.cyskat.de/dee/progxorg.htm)

I have not tried it as I find it easier to edit xorg.conf

Yes, it takes a little time and reading :(

The nvidia drivers come with a gui tool as well.

Again, to be of assistance it would help if we knew your monitors and video card.

---

### Post by Genius314 on 2006-12-20
> Again, to be of assistance it would help if we knew your monitors and video card.

Ok.
Lets see...
Video Cards:
ATI 3D Rage Pro 215GP
ATI 3D Rage I/II 215GT
Monitors:
MAG Innovision 17"
Compaq Presario MV700

I forget which card goes to which monitor, but I know the MAG monitor is the one that I'm using right now.

Also, does anyone know what DOSbox is? I need a version that will work with Ubuntu. I see a d/l for other distributions, but none that will work. I also tried using Wine to install the Windows version, but it didn't work (chances are, I did something wrong.)

---

### Post by macogw on 2006-12-20
If there's a d/l for Debian, it should work.

---

### Post by Genius314 on 2006-12-20
Ok, now I feel like I'm doing something completely stupid. I installed the Debian version of DOSbox, but now I can't find where it installed to. It isn't in the "Add/Remove" list either. Did it actually install, or did I just lose it? :-k

---

### Post by lyceum on 2006-12-20
> **Genius314 said:**
> Ok, now I feel like I'm doing something completely stupid. I installed the Debian version of DOSbox, but now I can't find where it installed to. It isn't in the "Add/Remove" list either. Did it actually install, or did I just lose it? :-k

Do you have the debian option under applications? You should see it there if nowhere else

---

