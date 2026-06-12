---
title: "Heeelllllllllppppppppp!!!!!!!!!!!"
date: 2007-12-07
forum: Apple Intel Users
---

### Post by Mac_bama on 2007-12-07
Hello all :) 

I decided to get the Mac I always wanted, and then realize my company's app doesn't run on Mac (even the internet explorer). 

I installed Parallels and created two virtual Machines 

One runs Windows XP with SP2 and the other Ubuntu (a friend help me installed it) 

Everything seems to run find but I did not get to use the Ubuntu a lot. 
With the advent of the new Mac OS Leopard I decided to upgrade. 

After the upgrade I couldn't start the Ubuntu. Actually it will startup but will get stuck during the booting process.

I decided to uninstall and reinstall. How difficult could it be? 

I have been trying for the last three days to install Ubuntu on a new VM.

The installation progresses smoothly until it gets to about 90% where it says 

Installing system 
Detecting hardware please wait...............

Loading module 'piix' for Intel Corporation 82801BA IDE U...............

Nothing else happens.

This is what I am trying to achie

I want to create a VM running Ubuntu on a Mac OS X Leopard.

Apart from the normal file system 

I want the root file system to 4 GB
Swap 2 GB

Three extra mount points...

/u01
/u02
/u03

I am using feisty 7.04

---

### Post by mert on 2007-12-07
As far as I know, feisty should run fine on parallels although I think there are some problems installing gutsy.  Make sure your RAM setting in the VM is 512 MB or less and try again.

---

### Post by chattrhand on 2007-12-07
> **Mac_bama said:**
> Hello all :) 

I decided to get the Mac I always wanted, and then realize my company's app doesn't run on Mac (even the internet explorer). 

I installed Parallels and created two virtual Machines 

One runs Windows XP with SP2 and the other Ubuntu (a friend help me installed it) 

Everything seems to run find but I did not get to use the Ubuntu a lot. 
With the advent of the new Mac OS Leopard I decided to upgrade. 

After the upgrade I couldn't start the Ubuntu. Actually it will startup but will get stuck during the booting process.

I decided to uninstall and reinstall. How difficult could it be? 

I have been trying for the last three days to install Ubuntu on a new VM.

The installation progresses smoothly until it gets to about 90% where it says 

Installing system 
Detecting hardware please wait...............

Loading module 'piix' for Intel Corporation 82801BA IDE U...............

Nothing else happens.

This is what I am trying to achie

I want to create a VM running Ubuntu on a Mac OS X Leopard.

Apart from the normal file system 

I want the root file system to 4 GB
Swap 2 GB

Three extra mount points...

/u01
/u02
/u03

I am using feisty 7.04

:) Hi Mac_bama
I am using a MacMini duocore 2GByte RAM and MacOSX10.4.11 (Tiger)
Under Parallels i am running KanotixEaster2006 which survived the upgrade to build 3214.

I also installed WinXP on a Parallels VM and also a AOL Windows client. Unfortunately my Windows serial code did not work, so this VM expired after 30 days.

Just for kidding I also installed a Win98 on Parallels VM, the serial code was accepted and it works fine.

I tried some Ubuntu versions on Parallels, but they used only 1280x1024 of my screen.

Now I tried Ubuntu Live CD direct booting on MacMini and found this results:

7.04 Feisty: 1280x1024 screen, builtin harddisk RO accessible,
sound, net, printer, usb-sticks, usb harddisk working fine.

7.10 Gutsy Gibbon: full 1680x1050 screen, builtin harddisk *not*  accessible,
sound, net, printer, usb-sticks, usb harddisk working fine.

8.06 Hardy Heron: full 1680x1050 screen, builtin harddisk accessible with root password,
sound, net, printer, usb-sticks, usb harddisk working fine.

I hope this would help you


chattrhand

---

### Post by Mac_bama on 2007-12-12
Thanks to all those who replied. I tried your solutions and it still didn't work........ but guess what i just went out and got me a VMware fusion and it works fine. Now its time to install oracle.

---

