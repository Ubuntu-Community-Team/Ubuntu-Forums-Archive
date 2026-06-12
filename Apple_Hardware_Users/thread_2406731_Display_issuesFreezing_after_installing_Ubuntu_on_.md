---
title: "Display issues/Freezing after installing Ubuntu on an iBook G3 notebook system."
date: 2018-11-24
forum: Apple Hardware Users
---

### Post by jharris1993 on 2018-11-24
Greetings!

**_Issue_:**
After installing Ubuntu 16.04 (PPC) on an iBook G3, with 640 megs Ram, using the minimal/network install disk, I end up with an unusable display, no virtual terminals, and a system that can only be shut-down by holding the power button down for 4+ seconds.

----------------------

I am the proud owner of an iBook G3, 640 megs RAM, and (as far as I know), a totally stock system except I installed a larger hard drive.

The system works.  I had Tiger 10.4n installed on it and it worked "perfectly" as far as that goes.  It also had a working installation of Ubuntu 10.n.  Both of those systems were so old that they were unusable.  I decided to install a more modern system on it and went through a number of iterations, including OpenBSD, and every installation ended up with the same result.

My  system goes through the boot process and ends up with an unusable  screen that looks like either a cloud nebula or an impressionist's  painting after he took drugs.  Unfortunately, I do not even get a text  based login, so any suggestions to edit my such-and-so.conf or something that requires a text based console is not possible.

Also note that every other *nix system I have tried installing on this system produces the exact same post-install display.  Re-installing Tiger produces a working system.

I have read many different forum threads, and have tried so many things including booting through the Open Firmware, that I am all but literally dizzy.  Of course, it is entirely possible that someone's solution from a thread I read four-or-five days ago might end up fixing it, so if there seems to be an "obvious" answer, please suggest it.

I don't want to just toss this system to the wolves, (or use it for target practice), so I would appreciate any help anyone could provide.

Thanks!

Jim "JR"

**_ Partial list of authorities_:**
I am sure that there are other sites that I consulted that I do not remember.
There is a whole other list of sites I consulted when trying to install OpenBSD that I don't remember as well.

[https://ubuntuforums.org/showthread.php?t=1516077&page=3&highlight=ppc+display](https://ubuntuforums.org/showthread.php?t=1516077&page=3&highlight=ppc+display)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
[http://forums.debian.net/viewtopic.php?f=16&t=26577&sid=955c352ea708a8f56f47e94b1c2927cf&start=15](http://forums.debian.net/viewtopic.php?f=16&t=26577&sid=955c352ea708a8f56f47e94b1c2927cf&start=15)
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[https://www.debian.org/ports/powerpc/inst/yaboot-howto/index.en.html](https://www.debian.org/ports/powerpc/inst/yaboot-howto/index.en.html)
[https://help.ubuntu.com/16.04/installation-guide/powerpc/](https://help.ubuntu.com/16.04/installation-guide/powerpc/)
[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/PPC](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/PPC)

---

### Post by jharris1993 on 2018-11-30
Update (as this may not have been clear in the original post):

A reboot progresses through the OF boot process correctly and I get the yaboot prompt where I can, and have, tried various parameters.  After yaboot, the screen becomes unusable and no virtual terminals work.

---

### Post by gsahli on 2018-12-01
I had exactly the same result on my PM G4 MDD - with a Radeon graphics chipset. I can't be sure you will have the same result, but try this at initial boot:
Linux radeon.agpmode=-1 modprobe.blacklist=ams #####(this is the boot> entry, type all as is, including spaces, not the ##)

If it works, put >append="radeon.agpmode=-1 modprobe.blacklist=ams"< into yaboot.conf

---

### Post by jharris1993 on 2018-12-01
@gsahli 
Thank you!

You are correct. I did not specify that this device has Radeon graphics hardware. 

I am not sure where to find the "amsXXXX" entry you specified. Is it something within the Mac's device display utility? Do I find it via open firmware?

Should the "blacklist" parameter work directly from the yaboot command prompt during boot-time?

Thanks again for all your help! 

Jim "JR"

---

### Post by gsahli on 2018-12-01
First time starting up, put those two arguments on the "Linux" command line. (DO NOT type the ###s - pound sign/hash tags are the typical comment start in linux)
Again - at the yaboot boot> prompt, type 
Linux radeon.agpmode=-1 modprobe.blacklist=ams

---

### Post by jharris1993 on 2018-12-03
Ahh! Now I understand. 

In the past I've seen "[command]####" used to indicate  some command followed by a string of digits, like "ams1234", so I was wondering what the digits could be.

Thanks for clarifying that.

---

### Post by jharris1993 on 2018-12-03
I tried what you suggested, and it did not work. I would post pictures, but there seems to be no way to do that via the mobile site.

---

### Post by gsahli on 2018-12-05
At the boot> prompt, try "Linux 3"
I'm hoping this takes you to a terminal/commandline so you can do further troubleshooting.

---

### Post by jharris1993 on 2018-12-05
Update:

I found an article somewhere that suggested "radeon.modeset=0", which I tried.  Once I did that, I was able to get a usable text-based system that I could log-into.  I ran into networking problems, other display problems, and a host of other things - so I decided to "drop back 10 and punt".  In other words, I was wondering if the installation was defective somehow so I re-installed with the 16.n LTS alternate disk and did a full-up install.

About a half-day later after everything was installed. . . . . .

I ran into some annoying, (but trivial), problems with kernel modules not loading (thermal_windtunnel didn't exist) and one or two other tweaks that I don't remember.

Booting now produces a black screen with a cursor, (arrow-pointer), that responds to the mouse, but no background, no graphics, or anything even resembling a desktop.  ALT-OPT [F-key] brings up a text session that I can log into and work with.

Any modeset other than "nomodeset" or "radeon.modeset=0" produces a frozen machine with no terminals available and a psychedelic screen display.

Apparently the 16.n install worked better than the 14.n install I tried before as ***nothing*** worked there.  I'm being offered the opportunity (on the text login screen) to update to the latest 18.n LTS version and I am tempted, however after spending about four hours installing 16, I hesitate to jump through additional hoops only to find that my system is worse off than before.

Note that I re-tried all of the other "video=" parameters, etc., with no success.

Any additional help would be appreciated.

Jim "JR"

---

### Post by gsahli on 2018-12-09
My only other suggestion is to create an /etc/X11/xorg.conf like this:
```

Section "Device"
	Identifier "Radeon"
	Driver "radeon"
EndSection 
```

---

### Post by jharris1993 on 2018-12-21
Gsahli,

Forgive my late reply - my wife's tablet crashed and I had to spend time fixing it.

There have been some interesting updates since I've posted last.

First of all, I replaced the device's CD drive with a DVD drive so that I could try installing from the "Live" DVD media.

1.  I have determined that the only, repeat *only*, way to get even a remotely usable display is to use the kernel parameter "radeon.modeset=0"
2.  ANY other combination of kernel parameters that does NOT include "radeon.modeset=0" *ALWAYS* produces a cloud nebula display.  Trust me, I have tried literally dozens and dozens of kernel parameters, in just about every combination available.  (e.g. radeon.modeset=-1, (or any "modeset" that is NOT equal to zero), video=ofonly, radeon.dpm=off, video=[display resolution], and so-on.)
3.  If I use "radeon.modeset=0" when booting the Live DVD for 16.n, I eventually end up with a display broken up into a zillion tiny pixel-dots that look like the screen is being viewed through a coarse window-screen.  This display, though barely visible, is useless because windows that are opened do not display any content.
4.  After installing the alternative CD, using the "radeon.modeset=0" kernel parameter (and baking it into the yaboot.conf file),  produces a working command-line interface.
5.  After logging into the command line interface, attempting to configure X produces an error something like "number of screens does not equal number of detected displays" and then fails with nothing else to guide me.

What frustrates me is that, (it seems that), everyone else appears to be able to install Lbuntu 16.n on woefully underpowered iBook G3 hardware - with less memory than I have and microscopic hard drives.  If they *DO* have issues, they wave their magic wand of kernel parameters and - magically! - they have an ultra-HD display, super-definition sound, it cooks breakfast and washes the laundry, their wives don't bitch at them anymore, etc. etc. etc.

In my own case, I have tried literally dozens and dozens of parameters, in just about every combination possible, threatened, cajoled, burned brown rice, sacrificed small rodents, and have all but driven myself over-the-edge trying to get this thing working.

Please forgive any frustration or sarcasm, my patience has been woefully tried.  If you - or anyone else - have any ideas that might help, please let me know before I smash  this thing into a zillion pieces!

---

### Post by jharris1993 on 2018-12-23
Update:

I get an unusable graphics display, but can get into a terminal session via alt-F1.

I can (apparently) stop the X server, but when I try to manually reconfigure X using the dpkg reconfigure command, nothing happens.

All the research I have done so far suggests that I should either use dpkg reconfigure, or that dpkg reconfigure has been depreciated and we're expected to use some alternate method - that apparently depends on a working GUI - however if you *don't* have a working GUI, you apparently are without help.

I'm going to start a different thread on that topic.

---

### Post by gsahli on 2018-12-26
Read this:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
They recommend installing lubuntu or xubuntu in order to get a lighter-weight desktop. From 16.04 onwards, the installer is supposed to figure out the xorg.conf stuff, and xorg.conf isn't necessary. I suggested the very simple xorg.conf, just to assure the radeon driver is used.

---

