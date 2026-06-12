---
title: "HELP!!! Powerbook G4 won't boot!"
date: 2008-11-25
forum: Apple Hardware Users
---

### Post by meatball68 on 2008-11-25
If anyone can help me with my problem that would be great. I'm going a college final project in our Linux class, I have a Mac PowerBook G4 Titanium 550 with 256 Ram, 20Gb HDD running OSX 10.3. The project is to get ubuntu loaded on this machine so I can run WINE indor to use MS Office 2003 for my power point presention. I tried alot of different installs in the past week and got nowhere. I loaded ubuntu 8.04.1 alternate-powerpc.iso on it(the less than 348 GB of RAM version) and installed with the video only mode, it took for ever to load, then when it rebooted, it flashed the screen the screen 5 times and left me this message:

Loading, please wait...
bog1_init failed: EXPLODE
screen init failed
kinit: name_to_dev_t(/dev/hda5)=(hda5(3,5)
kinit: trying to resume from /dev/hda5
kinit: No resume image, doing normalboot...
Ubuntu 8.04.1 unbuntu tty1
ubuntu login:

It looks like I can get a root shell up to try and fix but not sure how. I tried rebooting several times and I either get the above message or just a blinking cursor in the upper left corner. If anyone has any suggestions please HELP !!

---

### Post by ubuntubrian on 2008-11-25
Ouch! I can say that every release since Dapper has had major problems and booting the install cd or the live cd is one of them. I recommend getting a Dapper live cd and see if that will boot. It was the last officially supported version by Canonical.
As faras wanting to run Wine, you can't on a PowerPC. There are no emulators running on Linux, assuming that you get it installed, other than Mac-on-Linux or QEMU that will run on PPC. MOL won't help as it only runs Mac OSes and QEMU is so slow as to be useless. There is an accelerator, KEMU, but it won't install on any PPC Linux distro.
However, if you can get Dapper installed you can then install Open Office which has a Presentation software that will run PowerPoint and any other MS Orifice apps.
I don't recommend upgrading past Dapper until you are done doing any time important work as those upgrades have been brutal on my TiBook.
BTW, here's the Dapper Desktop cd link:

[http://releases.ubuntu.com/dapper/](http://releases.ubuntu.com/dapper/)

Download it and then burn it to an .iso. that's not too easy either (in OS X) but hopefully you know what you are doing. There are some freeware apps that will run in OS X that can burn a cd image.

---

### Post by stream303 on 2008-11-25
Well, it's booting - the big problem is that the gui desktop needs manual configuration.

Did you free up sufficient space for a partition to hold the entire contents of Ubuntu beforehand?  Makes me wonder if the installer just found some small free space and had a go at it by itself. :)

But you may want to reconsider going any further.  AFAIK, Wine isn't supported on PPC.  Somebody correct me if I'm wrong.  And with only 256mb ram, it may not run efficiently enough to drive you out of your mind with powerpoint if it could run in the first place.

update: Looks like Ubuntubrian beat me to it! :)

If this is a project for a Linux class, perhaps the *coolest* thing you can do is not to use MS, but download NeoOffice, which is a great port of OpenOffice, and use it's presentation module.

[http://www.neooffice.org/neojava/en/index.php](http://www.neooffice.org/neojava/en/index.php)

OpenOffice is great, but the NeoOffice port has many advantages going for it, especially with PPC and older versions of OSX.

Not many Linux users are running MS Office, so this might be just the ticket without having to do anything to your laptop!

Heh, then again, if you are going to go to all this trouble, you might as well load Ubuntu and just use OpenOffice that comes with it....

So the big question is:  how are your partitions and are you willing to dual boot, or dedicate the whole machine to Ubuntu - keeping in mind this is a *final* for a Linux class?  Hope you have some coffee on hand. :)

---

