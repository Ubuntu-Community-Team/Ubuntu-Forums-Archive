---
title: "1920x1200 on live cd"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by gar710 on 2007-05-08
Greetings,

  I'm fairly new to Linux, very new to Ubuntu. I've been trying various distros to see which agrees with my hardware and which do not. So far I'm 0 for 3.  The live cd does not recognize my ATI radeon 9500 pro card  nor offers 1920x1200 resolution(Dell 2407wfp monitor). Activating the restricted ATI drivers only offers 1600x1200 resolution. I've spent too many hours scouring google for answers, but most is too advanced for me to understand at this time. 


I downloaded the ati drivers from their web site, but I get this message when opened:

"Could not open the file /home/ubuntu/Desktop/ati…ler-8.36.5-x86.x86_64.run. 

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

I'm stumped.


At this point, I simply want to know if 7.04 will work with my hardware before installing, not after. I've read much about the blame game about ati drivers and linux, and I really don't much give a hoot who blames who, I just would like to use the software on my hardware. For reference , one distro, pclinuxos, had no problem recognizing my card or detecting the correct resolution the from the first try of the live cd. Unfortunately, it won't work with my funky dell modified creative live sound card in my Dell 4550.

Hey, I realize I may be in over my head right no if Linux is this difficult to use and I need to type in code. Not a knock on anyone, just a personal assessment . It's great the software is free to use .... if you know how to use it :)  I do not.

I'm grateful for any answers .

-regards

---

### Post by gar710 on 2007-05-09
Anyone ?

---

### Post by derekguy on 2007-05-09
have you checked the permissions on the .run file? Make sure it can be executed as a program. 

You are wise to try Ubuntu first but I can say that the learning curve to get used to Ubuntu is steep if you want to tweak things to work perfectly.

---

### Post by gar710 on 2007-05-09
> **derekguy said:**
> have you checked the permissions on the .run file? Make sure it can be executed as a program. 

You are wise to try Ubuntu first but I can say that the learning curve to get used to Ubuntu is steep if you want to tweak things to work perfectly.


That's a good point , I'll check  and give it another go.  Yes, it seems it takes some work, but I figure I have to start somewhere :)   I'm using XP now , but as reliable as this Dell machine has been for 4 and a half years, I'm preparing for my next computer.  I see a crossroads coming, build my own or another Dell ..... and if it's another Dell, windows or linux.  If I'm going to use linux , I expected some difficulties . so I thought I'd see if it's for me or not sooner rather than later and be forced to decide in the dark , so to speak.

Thanks for the tip.

---

### Post by Outrunner on 2007-05-09
I don't think there's much point in installing the drivers anyway, since you are running the live CD. But if you must try(dunno if it will work at all, but w/e)

```
sudo sh Desktop/*.run
```

in the terminal. I assure you that after you install, you'll be able to get your desired resolution.

---

### Post by Terl on 2007-05-09
Have you thought about installing Ubuntu?  Some of the settings, like your resolution, require editing of a file to get all the resolutions available that you can run.  The live cd does a good job with a lot of this but is not as configurable as an installed system.  

You mentioned the ATI driver issue.  Sadly the linux driver support is not as good for ATI as it is for nVidia.  There are drivers for your card and there is much documentation here as to how to get it all working.  The xorg.conf file (that drives your x configuration) has a section for the monitor.  It is editable and can be fixed to match your monitor's capabilities.  I do not know how to do this and make it work for a system running from the live cd though. 

Just as a sidenote also there has been press that Dell will be selling pc's with Ubuntu as an option. :)

---

### Post by ahmatti on 2007-05-09
Here is a thread with some instructions about the dell monitor [http://ubuntuforums.org/showthread.php?p=1489308](http://ubuntuforums.org/showthread.php?p=1489308)

---

### Post by gar710 on 2007-05-09
Thanks for all the replies,

Yeah, I thought I may get into a catch 22 here.  I can't get my monitor to work properly without installing the software, but I thought the live cd function was there to see if your hardware would work -before- installing.  

If I had a spare hard drive I'd just install it on that. I've only got 20gb left on my original 60gb pata drive though, and since pata drives are going by the wayside, I can't see investing in technology that's going away fast..  I'd buy a sata drive, which I could use in the future, but using it on this older system may not work so well because I'd need some kind of ide/sata adapter, which are usually less than solidly reliable .  This system cannot boot from a usb drive either.  

The ati drivers won't install of course(on the live cd). I'm sort of in over my head on this, as I said. I'm spending all my time just trying to get it to work properly, this was not my original intention .  If Dell does start selling some pc's with ubuntu, hopefully they'll have all this configuring stuff worked out or else it will be a giant can of worms for them. 

Anyways, thanks again.

---

### Post by gar710 on 2007-08-29
Well, I've installed it on my Dell 4550, and guess what, nothing has changes. I have the ATI Accelerated graphics driver enabled, but it does nothing. I'm stuck with 1024x768 resolution on a Dell WFP2407 1920x1200 screen .  

Why does getting the screen resolution have to be so difficult with Ubuntu ?  

I read thread after thread of no 1920x1200 , not mention others too.

Why ?  I just don't get this.

I tried this [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b)

but depite that ATI accelerated graphics being enabled, checked and restarted, gksudo gedit /etc/default/linux-restricted-modules-common in terminal: 

gksudo gedit /etc/default/linux-restricted-modules-common(gedit:7299): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.



 I get this in gedit :, it tells me it is disabled:

 This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables both the nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES=""

What to do then ?

---

### Post by armandh on 2007-08-29
the catch 22 answered
find an old 10G Hdd and do a practice install.
it is what I did with gutsy. 
I now have the feisty drive pluged back in.
I am not quite ready for the next gen.

---

### Post by gar710 on 2007-08-29
This is a drive I can spare. I have my original disc uninstalled , as well as another external drive with everything backed up.

I'm still getting no where with Ubuntu.  It seems you need to be an expert to get your hardware to work.

I'm following : [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

but i get errors, it doesn't help with errors.

sudo apt-get install xorg-driver-fglrx
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
garth@garth-desktop:~$ sudo depmod -a
garth@garth-desktop:~$ sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper \
> debconf libstdc++5 linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
module-assistant is already the newest version.
build-essential is already the newest version.
fakeroot is already the newest version.
dh-make is already the newest version.
debhelper is already the newest version.
debconf is already the newest version.
libstdc++5 is already the newest version.
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
garth@garth-desktop:~$ sudo bash ati-driver-installer-8.40.4-x86.x86_64.run --buildpkg Ubuntu/feisty
bash: ati-driver-installer-8.40.4-x86.x86_64.run: No such file or directory

---

### Post by gar710 on 2007-08-29
The downloaded ATI driver does not run .


I try to run it, but nothing. I guess they're not for Ubuntu ?

What is ?

---

### Post by mysticmatrix on 2007-08-29
If you have got your drivers installed correctly according to the ubuntu wiki page, then we can help if you post the output of following command 

```
cat /etc/X11/xorg.conf
```

Also tell horizontal and vertical refresh rate of your monitor. If you are not sure, just give us exact model of your monitor and we'll try to find them out. 

Also, if your drivers are correctly installed, don't try to mess with them further.

---

### Post by gar710 on 2007-08-29
As I stated, I made it to this step"DISABLED_MODULES="fglrx",
but I can't get past this step :

 sudo dpkg -i xorg-driver-fglrx_8.40.4-1*.deb \
> fglrx-kernel-source_8.40.4-1*.deb \
> fglrx-amdcccle_8.40.4-1*.deb
dpkg: error processing xorg-driver-fglrx_8.40.4-1*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-kernel-source_8.40.4-1*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-amdcccle_8.40.4-1*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx_8.40.4-1*.deb
 fglrx-kernel-source_8.40.4-1*.deb
 fglrx-amdcccle_8.40.4-1*.deb

So, no , I can't install the drivers properly. What do I do from here ?

---

### Post by gar710 on 2007-08-29
Ubuntu's not for older hardware with an ATI card .  Too bad :)

I give up on this, I've been at it for days.  I shouldn't have to devote my life to trying to get my pc to work with Ubuntu.  I thought this software was supposed to be so great ?   Not for a desktop user.

Thanks for replying.

---

### Post by mysticmatrix on 2007-08-29
> **gar710 said:**
> Ubuntu's not for older hardware with an ATI card .  Too bad :)

I give up on this, I've been at it for days.  I shouldn't have to devote my life to trying to get my pc to work with Ubuntu.  I thought this software was supposed to be so great ?   Not for a desktop user.

Thanks for replying.

Yes, if only you knew that resolution problems have nothing to do with your graphics drivers, as you had once got your drivers installed correctly.
Well, come back for Gutsy which has a easy noob tool for configuring resolutions.

---

### Post by mysticmatrix on 2007-08-29
> **gar710 said:**
> Well, I've installed it on my Dell 4550, and guess what, nothing has changes. I have the ATI Accelerated graphics driver enabled, but it does nothing. I'm stuck with 1024x768 resolution on a Dell WFP2407 1920x1200 screen .  

Why does getting the screen resolution have to be so difficult with Ubuntu ?  

I read thread after thread of no 1920x1200 , not mention others too.

Why ?  I just don't get this.

I tried this [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b)

but depite that ATI accelerated graphics being enabled, checked and restarted, gksudo gedit /etc/default/linux-restricted-modules-common in terminal: 

gksudo gedit /etc/default/linux-restricted-modules-common(gedit:7299): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.



 I get this in gedit :, it tells me it is disabled:

 This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables both the nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES=""

What to do then ?

Once you got your drivers working, a simplae edit of /etc/X11/xorg.conf would have done the job.

---

