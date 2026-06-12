---
title: "PowerPC G3"
date: 2009-12-05
forum: Apple Hardware Users
---

### Post by intrepid93 on 2009-12-05
I got a MAC powerPC G3 for free. It looks really old but I want to get some Linux for it. I'm not really sure which version.
 
RAM: 4*512MB (2GB, all slots filled.)
CPU: No idea, I took the heatsink off and it didn't say.. The HS is really small so I guess the CPU is aswell.
GPU: Old workstation one.. The computer was used for graphic design a long time ago.
It currently has Mac OS X server installed and has An E-ATX motherboard.
 
I want to be able to access the internet, have a simple desktop. Have the flash plugin.. Can't think of much else at the moment.
 
Will the mac just boot off the disk if I put the disk in and restart it???

---

### Post by linuxopjemac on 2009-12-05
You first have to find out if it's Oldworld or Newworld Mac. I guess it's Oldworld, meaning you have to boot from BootX. 

General info on Newworld Macs and yaboot/ybin:
[http://mac.linux.be/content/booting-newworld-macs-yabootybin](http://mac.linux.be/content/booting-newworld-macs-yabootybin)

some info on installation:
[http://mac.linux.be/content/installation-linux-ppc-based-macs](http://mac.linux.be/content/installation-linux-ppc-based-macs)
[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)
[http://ubuntuforums.org/showthread.php?t=1330343&highlight=oldworld](http://ubuntuforums.org/showthread.php?t=1330343&highlight=oldworld)

---

### Post by intrepid93 on 2009-12-05
It is definetly oldworld. 

Thanks looking at installation info now.


> If you've ended up at this page, you're probably about to do something irrational: install Linux on an OldWorld Mac.
> You should read the whole thing at least once before proceeding, to get a feel for what you're wading into. Then, take a Zen moment and accept the possibility of failure. This might not work on your system.

EEK!!

> 3) Install the original OS (quite likely pre-OS 9) from the Software Restore disk, then turn right around and do a clean installation of OS 9 from your OS 9 disk. 
Don't have.


ALso... I don't have the password for this machine. It was going to be put in the trash!!! so I took it.

---

### Post by linuxopjemac on 2009-12-05
you need MacOS, otherwise you won't be able to boot. What you can do is download a free version of MacOS 7.something...I will have a look for you.

---

### Post by linuxopjemac on 2009-12-05
start with 7.0, update to 7.01 and then you go to 7.5.3...it's a lot of work, I hope you have a lot of time ... and if you have Linux running at the end it will be terribly slow...

[http://download.info.apple.com/Apple_Support_Area/Apple_Software_Updates/English-North_American/Macintosh/System/Older_System/System_7.0.x/](http://download.info.apple.com/Apple_Support_Area/Apple_Software_Updates/English-North_American/Macintosh/System/Older_System/System_7.0.x/)

[http://download.info.apple.com/Apple_Support_Area/Apple_Software_Updates/English-North_American/Macintosh/System/Older_System/System_7.5_Version_7.5.3/](http://download.info.apple.com/Apple_Support_Area/Apple_Software_Updates/English-North_American/Macintosh/System/Older_System/System_7.5_Version_7.5.3/)

you might consider to buy a 2nd hand MacOS8 or 9 CD, much easier...

---

### Post by igor_av on 2009-12-05
Are you sure it's an Oldworld mac? Oldworld computers didn't have ATX motherboard, couldn't handle 512 Mb memory modules, and surely couldn't run Mac OS X server (unless it's a pre-X version, which is quite rare). What is the case color : beige, blue or grey?

Also, if you want to use the installed system, look on the net for the procedure to reset the root password on mac os x.

---

### Post by intrepid93 on 2009-12-05
> Are you sure it's an Oldworld mac? Oldworld computers didn't have ATX motherboard, couldn't handle 512 Mb memory modules, and surely couldn't run Mac OS X server (unless it's a pre-X version, which is quite rare). What is the case color : beige, blue or grey?

Well I just guessed it ws E-ATX because it is a big motherboard. Larger than standard atx today. Also the proccesor heatsink is about the same size or a bit smaller than a pentium III heatsink and has no fan! that's what made me think it was old world. It musn't be old world if they couldn't handle 512mb modules then..

This is what it looks like:
[IMG]http://www.applematters.com/assets/images/uploads/old/products/cache/Power_Mac_G3_BW_300x405.jpg[/IMG]
> Also, if you want to use the installed system, look on the net for the procedure to reset the root password on mac os x.
They say to hold down Apple-s while it restarting or booting and then type some stuff once you get to a screen with text on it. I can't reach that screen. I don't have a apple keyboard although Ctrl-S is the same as Apple-s isn't it??? Well I still can't reach the screen.

> start with 7.0, update to 7.01 and then you go to 7.5.3...it's a lot of work, I hope you have a lot of time ... and if you have Linux running at the end it will be terribly slow...

[http://download.info.apple.com/Apple.../System_7.0.x/](http://download.info.apple.com/Apple.../System_7.0.x/)

[http://download.info.apple.com/Apple...Version_7.5.3/](http://download.info.apple.com/Apple...Version_7.5.3/)

you might consider to buy a 2nd hand MacOS8 or 9 CD, much easier...
I was just hoping like on new pc you could just put the ubuntu disk in and follow the easy setup.. I would actually rather just get the apple to work if I could instead of puting all the effort in to get ubuntu on it. Mostly because I know I will stuff something up along the way and have no OS installed...

---

### Post by Gen2ly on 2009-12-06
Ah, that's a new world mac.  The general run is that anything made around the time Steve Jobs returned is new world.  Best way to go, and I dont' want to sound discerning, would be to use a Debian CD and install a lightweight desktop on it.  Installing Ubuntu's GNOME is really gonna challenge that machine.  Personally I'd recommend LXDE which I got on my 300Mhz ibook and it runs great, there is also XFCE that offers more options.  Good luck, tell use how it goes.

---

### Post by intrepid93 on 2009-12-06
OK so what light weight desktop do you reccomend and do I need to do anything besides just going throught the installation on the CD/DVD??

---

### Post by Gen2ly on 2009-12-06
intrepid93, because this is an older Apple computer it's going to take a little more time, and time to learn how to install.  If you're pretty new to computers, you might want to consider just trying the Ubuntu CD that will install the GNOME desktop.  However, if you're up to the task, I'll put this up (because I think that you'll probably find, like me, that GNOME requires too many resources for this type of computer):

The Debian netinstall CD will install just the basic system and you can choose the desktop you want.  Ubuntu is based on Debian so you ask questions here and likely get them answered.

[LIST=1]
[*]Download the [Debian netinstall CD](http://www.debian.org/CD/netinst/).
[*]Burn, boot CD.  Because you have an older computer, you may have to boot the CD directly from the Open Firmware (like BIOS for Mac) by holding **Apple**+**Option**+**O**+**F** at first boot.  Then enter 'boot cd:,\install\yaboot' to boot.
[*]Follow the instructions and install.  Not sure if you can specify desktops here like LXDE, been awhile, maybe someone can help.
[*]Reboot, login.  You will be in the console (text-mode).  From here you can install other software.  If you want to install LXDE type:
[/LIST]

```
apt-get install lxde
```

If you get this far, let us know, there are a few other things you'll probably need to know.

---

