---
title: "Brand new user -only two problems"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by tonywatts on 2006-08-15
Hello all, first post of many I'm sure.  I've just successfully installed the latest version of Ubuntu, but am experiencing two teething problems, with one most likely easily solved once the other's ok:

1) Connecting to the internet

My broadband subscription is through Tiscali, who helpfully provided a budget modem and installation CD.  These were easy enough to set up in the operating system they expected, but I have no idea where to start with Linux.

2) Extra-low resolution

My monitor supports the usual 1024 x 768 resolution, but Ubuntu seems insistent that my only option is a res of about half this.  I'm using an ATI Radeon x600 Pro graphics card on PCIx16 and expect the correct driver would be easy enough to find and install, solving this problem in a matter of seconds.  If that's the case, a URL would help me along greatly.  I'm not sure whether I could download the Linux driver through XP though.

Hopefully two simple problems to solve, and any help would of course be appreciated.

To finish, a more opinion based question: is there any point in me installing more than one distribution of Linux at a time? e.g. Ubuntu and Suse, just so I can get a feel for what's the same and what's different...

Cheers in advance,

Tony

---

### Post by Kobalt on 2006-08-15
1. We need to know what kind of modem you have : is it an ethernet ? a router ? 

2. To configure your resolution, type in command line :
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
make sure to chose the resolutions you want to be able to chose afterwards using the space bar, then restart X with Ctrl+Alt+Backspace, and that should be it. 

Cheers !

---

### Post by Kobalt on 2006-08-15
I forgot about you last question : you could get an advantage of installing another distro if you want to experiment yourself into compiling apps or kernels etc... But if that's what you wish to do I would recommend at first using Ubuntu, get to knowing it and to be able to use it well. Then on another partition install a Gentoo and then learn on it. But keep your Ubuntu clean and working I suggest, so that you always have a running OS.

---

### Post by tonywatts on 2006-08-15
1) It's a [Thompson Speedtouch 330](http://www.speedtouchdsl.com/prod330.htm) modem.  Definitely not a router or similar, just a box with one end plugged into the splitter and the other into a USB port.

2) Cheers

---

### Post by Kobalt on 2006-08-15
Ouch, USB modem are a pain to get to work with Linux :confused: 

Here is a HowTo for configuring your modem :
[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)

And a thread discussing the installation process.
[http://ubuntuforums.org/showthread.php?t=212889](http://ubuntuforums.org/showthread.php?t=212889)

I hope it will help you. I assume your resolution problem is fixed then ? 

Cheers ! :rolleyes:

---

### Post by tonywatts on 2006-08-15
The res fix worked a dream, thanks.  I'm about to make a start on the modem.

Tony

---

### Post by Kobalt on 2006-08-15
You're welcome :)
Good luck to get your modem to work, keep us posted if you get it to work well.

Cheers ! :rolleyes:

---

### Post by tonywatts on 2006-08-15
Ah, okay, I didn't last long.  Without the modem working in Ubuntu, I can only download the firmware patch with XP, which can't then save it to my Linux partition.  Or can it?

Tony

---

### Post by Kobalt on 2006-08-15
The simplest way for you is being able to access your windows partition from Ubuntu, so that you can download you drivers from Windows and then access it from Ubuntu. 
Here is a way to get to do that : 
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

I told you getting USB modems to work was a pain :) But still, accessing your Windows partition from Ubuntu can be usefull, it's worth doing it anyway.

---

