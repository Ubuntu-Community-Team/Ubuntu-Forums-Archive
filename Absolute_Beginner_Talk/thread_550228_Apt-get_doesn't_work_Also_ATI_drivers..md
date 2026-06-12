---
title: "Apt-get doesn't work? Also ATI drivers."
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by Halifax on 2007-09-13
Here's what it says:

halifax@ASUS:/etc/X11$ gksudo apt-get update
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
halifax@ASUS:/etc/X11$ sudo su
root@ASUS:/etc/X11# apt-get update
E: The method driver /usr/lib/apt/methods/Http could not be found.
root@ASUS:/etc/X11#

I have no idea how this started. I was going to install drivers from here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Install_Beryl_using_Open_Source_drivers](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Install_Beryl_using_Open_Source_drivers)

but after I did the wget command (I just did a copy-paste), apt-get stopped working. Thinking as hard as I can, I cannot imagine anything else I could have done to break it.

Also, which is the best ATI driver for an x800?

---

### Post by mcduck on 2007-09-13
It's 'sudo apt-get update'. gksudo is for graphical applications, sudo for command line. Also to open a root session in terminal you'd better use 'sudo -i' as 'sudo su' or 'sudo -s' won't load root's profile correctly which might in some cases mess your normal user's profile..

Anyway, there might be something wrong with your sources.list file. Could you post here output of "cat /etc/apt/sources.list"?

edit: the best driver for X800 is Ati's own fglrx driver. The restricted Drivers-thing in System/Administration should be able to install the driver for you.

---

### Post by Halifax on 2007-09-13
halifax@ASUS:~$ sudo apt-get update
E: The method driver /usr/lib/apt/methods/Http could not be found.
halifax@ASUS:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [Http://security.ubuntu.com/ubuntu](Http://security.ubuntu.com/ubuntu) feisty-security multiverse
halifax@ASUS:~$    

I've added lines to the sources.list file before (to install ntfs-config and then for the link I posted already), but I deleted those lines once I was done (or once I relised that sometihng wasn't working ^_^).

---

### Post by Halifax on 2007-09-13
Wait, does this have something to do with the capilal H in Http? I know things are case sensitive in Linux...

---

### Post by Halifax on 2007-09-13
> **Halifax said:**
> Wait, does this have something to do with the capilal H in Http? I know things are case sensitive in Linux...

That was it. apt-get works now. ONE line had a capital H in it and it borked the whole thing.

Sorry for the trouble.

---

### Post by CaptainInsaneO on 2007-09-13
Good eyes! I sat here scratching my head for awhile and didn't even see that. :popcorn:

---

### Post by Halifax on 2007-09-13
One problem down.

Could anyone give me a recommendation on a good ATI driver for my x800xt? I've seen so much stuff about ATI drivers, but I can't find a comparison between the different drivers, so I don't know which one to try. I think I used to use the Mesa drivers before I reinstalled, and Beryl crashed every now and then, but I'm not sure if that was the fault of the drivers or Beryl...

---

### Post by CaptainInsaneO on 2007-09-13
You could give Envy a shot.

I use an nVidia 8800gts but it works great for me. I think it would do the same for you.

---

### Post by Paul133 on 2007-09-13
Yeah. fglrx. It should be in the restricted drivers manager.

---

### Post by sloggerkhan on 2007-09-13
If you want to game, use fglrx ati drivers.
The x800 works OK with open source drivers, but for most games,  the fglrx driver will be better.

If you don't game, currently the ati (open source) driver will work much easier with desktop effects.

---

### Post by Halifax on 2007-09-13
> **Paul133 said:**
> Yeah. fglrx. It should be in the restricted drivers manager.

Forgive me for being so terribly ignorant, but I can't seem to find that. The menus are a little different than how they were before (Ubuntu with KDE installed before, now it's a fresh Kubuntu install - I can't find things!). Restricted drivers manager is installed through Adept, but I can't find it.

---

### Post by Paul133 on 2007-09-13
Kubuntu? No idea. I use Gnome, and it's System -> Administration -> Restricted Drivers Manager

---

### Post by Halifax on 2007-09-13
Hello all. I just reinstall Ubuntu and then installed KDE on top of that. MUCH MUCH better. Some problems were solved from that alone, but I still need a good ATI driver. fglrx destroys everything it touches on my computer (read: it doesn't work). It's an ASUS ATI card, but ATI drivers should work just fine on it.

anyway, I'm trying Envy to see if it can have any better luck installing the drivers than I did.

One thing I thought was weird, though, was when fglrx crashed, I noticed it was referencing PCI 1:0:1 instead of PCI 1:0:0, and nowhere in xorg.conf did it reference PCI 1:0:1. It would always look to the wrong PCI location and say that there were "no screens found". Switching back to the "ati" driver fixed it, but I think my video driver is probably the reason I can't watch video files despite having all the necessary codecs.

---

### Post by huangweiqiu on 2007-09-13
Hi Bro

You can try ATI new driver

see more : [http://www.linuxine.com/2007/09/ati-video-card-new-driver-8417-release.html](http://www.linuxine.com/2007/09/ati-video-card-new-driver-8417-release.html)

---

### Post by Halifax on 2007-09-13
Well, installing the driver with Envy seems to have worked. It's a nice "do it for you" kinda program. Good for idiots like me! I can even watch videos now.

...though I still can't mount my USB HDDs so I can't watch ALL of them... ^_^

The USB thing seems to just be KDE, though, because it worked last time I was in Gnome.

...don't WANNA use Gnome, though...

Aah well, I'll stop bothering all of you with this and figure it out on my own.

...although, does anyone know how to fix the "Support for non power of two textures missing" and "glXBindTexImageEXT is missing" errors in Beryl? :)

---

