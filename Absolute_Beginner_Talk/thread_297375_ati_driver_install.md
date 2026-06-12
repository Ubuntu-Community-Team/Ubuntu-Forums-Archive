---
title: "ati driver install"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by loclei on 2006-11-11
here's what i get when i run sudo ./ati-driver-installer-8.30.3.run command:
Detected configuration:
Architecture: i686 (32-bit)
X Server: Unknown X Window
cp: cannot stat `x710/usr/X11R6/bin/*': No such file or directory
find: install/usr/bin/fireglcontrolpanel: No such file or directory

but the installation goes on.. so i guess that's not that big of a deal.. 

but then i have to do a sudo aticonfig –initial command and i get:
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-2

then sudo aticonfig --overlay-type=Xv and i get:
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-3

then sudo dpkg-reconfigure xserver-xorg

xserver-xorg postinst warning: not updating /etc/X11/X; file has been
   customized
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20061111091447

then To launch X, type start x
start: Need to be root

if i run sudo start x it says 
start: Unknown job: x

can someone pls tell me what i'm doin wrong?

and if i  write  Fglrxinfo
i should get this... 

The following should be displayed:

$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.5755 (8.24.)

but i get 

display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL
OpenGL version string: 1.2 (1.3 Mesa 6.5.1)

and also HOW TO SAVE THE X WINDOW like it says in this picture..

---

### Post by junglepeanut on 2006-11-11
Which version of ubuntu are you using?

Edgy (and therefore I believe Feisty too but I haven't checked yet) has issues with the default bash so you need to make a temporary link.

Also with some versions of the Ati installer I can only get them to work with x completely off and root "root" not via sudo.

Also it looks like you may have typed "start x" but should type

startx

The startx should still work with mesa driver I think but slowly. Also make sure you follow the wiki for removing old ati open source.

The root things has not failed me once.

---

### Post by junglepeanut on 2006-11-11
Also which ati card do you have?

---

### Post by loclei on 2006-11-11
> **junglepeanut said:**
> Also which ati card do you have?

i have ati radeon 9000 PRO II 128 mb 

and you can see in the second picture that if i run 
aticonfig --initial ....

could not find configuration file ...

[http://www.ubuntuforums.org/showthread.php?t=279240&highlight=ati+install](http://www.ubuntuforums.org/showthread.php?t=279240&highlight=ati+install)
[http://www.ubuntuforums.org/archive/index.php/t-243342.html](http://www.ubuntuforums.org/archive/index.php/t-243342.html)
these are the links i used in atempting to install the ati driver

---

### Post by msak007 on 2006-11-11
> **loclei said:**
> i have ati radeon 9000 PRO II 128 mb 

Not that this has anything to do with the errors you get when trying to run the installer, but you won't benefit from installing the driver. R200 chipset based cards are no longer supported as of driver version 8.29.6 released last month and you must use one of the open-source alternatives (either the "ati" or "radeon" driver). [Here's]("http://www.phoronix.com/scan.php?page=article&item=550&num=1") the whole article for reference, and a little snippet from it:

> Finally, with the 8.29.6 drivers it is  time that we say a final farewell to this R200 support. The rationale behind this  move was to spend more resources on increasing the stability and features for the drivers with post R200 hardware. The hardware officially dropped includes  the FireGL 8800/9200, Radeon 8500/9000/9100/9200/9250, and Mobility Radeon 9000/9200.

---

### Post by junglepeanut on 2006-11-11
Sorry ran out for a sec, msak007 beat me to it, that was why I asked about the card type.

I can continue to help you try configure the open source driver if you would like, but it should be fairly straight forward from the wiki. Or a similar type of thread.

Was there two pics before I only remember one...I must be getting blind?:)

---

### Post by loclei on 2006-11-11
> **msak007 said:**
> Not that this has anything to do with the errors you get when trying to run the installer, but you won't benefit from installing the driver. R200 chipset based cards are no longer supported as of driver version 8.29.6 released last month and you must use one of the open-source alternatives (either the "ati" or "radeon" driver). [Here's]("http://www.phoronix.com/scan.php?page=article&item=550&num=1") the whole article for reference, and a little snippet from it:

i have the 8.28.8 driver and it's the same problems.. 

even more of them

i guess i should try to uninstall the curent drivers.. then start all over again with the 8.28.8 driver
but how do i uninstall the ati driver?

---

### Post by loclei on 2006-11-11
i also tried this [http://www.ubuntuforums.org/showthread.php?t=180222&highlight=ati+driver+install](http://www.ubuntuforums.org/showthread.php?t=180222&highlight=ati+driver+install)
but i get a error when i update :

Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by loclei on 2006-11-11
> **WalmartSniperLX said:**
> I followed these instructions that I found on this forum. Here are the steps ive completed:

1.Install necessary tools:
Code:
sudo apt-get update 
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base

2.Create .deb packages:

Code:
chmod +x ati-driver-installer-8.26.18-x86.run
./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper

same installing procedure as in this link:
[http://www.ubuntuforums.org/showthread.php?t=279240&highlight=ati+driver+install](http://www.ubuntuforums.org/showthread.php?t=279240&highlight=ati+driver+install)


at 1 i get
```

sudo apt-get update
Errhttp://security.ubuntu.com edgy-security Release.gpg
  Temporary failure resolving &#8216;security.ubuntu.com&#8217;
Errhttp://security.ubuntu.com edgy-security/main Translation-en_GB
  Temporary failure resolving &#8216;security.ubuntu.com&#8217;
Errhttp://security.ubuntu.com edgy-security/restricted Translation-en_GB
  Temporary failure resolving &#8216;security.ubuntu.com&#8217;
Errhttp://security.ubuntu.com edgy-security/multiverse Translation-en_GB
  Temporary failure resolving &#8216;security.ubuntu.com&#8217;
Errhttp://archive.ubuntu.com edgy Release.gpg
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Errhttp://archive.ubuntu.com edgy/main Translation-en_GB
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Errhttp://archive.ubuntu.com edgy/restricted Translation-en_GB
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Errhttp://archive.ubuntu.com edgy/multiverse Translation-en_GB
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Errhttp://archive.ubuntu.com edgy/universe Translation-en_GB
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Errhttp://archive.ubuntu.com edgy-updates Release.gpg
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Errhttp://archive.ubuntu.com edgy-updates/main Translation-en_GB
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Errhttp://archive.ubuntu.com edgy-updates/restricted Translation-en_GB
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Errhttp://archive.ubuntu.com edgy-updates/multiverse Translation-en_GB
  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg)  Temporary failure resolving &#8216;security.ubuntu.com&#8217;
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;security.ubuntu.com&#8217;
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;security.ubuntu.com&#8217;
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_GB.bz2)  Temporary failure resolving &#8216;security.ubuntu.com&#8217;
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
```



at 2 i get

```

user@user-desktop:~$ sudo mv /bin/sh /bin/SH
user@user-desktop:~$ sudo ln -s /bin/bash /bin/sh
user@user-desktop:~$ ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/dapper
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/dapper
./packages/Ubuntu/ati-packager.sh: line 56: dpkg-architecture: command not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install

```

can someone help me?

---

### Post by junglepeanut on 2006-11-11
Sorry I fell asleep. You still haven't explicitly said which version you are using, but I am going to assume it is dapper since you are trying to install that from one of the lines in your code. If that is the case, why are you making the symbolic link for sh, I am not sure it should effect anything but it does not make sense to me to do it as this was the link change I was talking about if you had edgy in my first post, not for dapper. Also if you do have Edgy first remember Edgy is a testing platform. Then instead of making a symbolic link change for sh do it with the links as posted here NOTE

NOTE NOTE This is for Edgy 
[http://www.marteydodoo.com/2006/08/29/installing-binary-ati-drivers-on-ubuntu-edgy/](http://www.marteydodoo.com/2006/08/29/installing-binary-ati-drivers-on-ubuntu-edgy/)

Second, it looks like you are not connected to the Internet in some fashion or apt is messed up as you are not able to even update.

---

### Post by loclei on 2006-11-11
yes i have some sort of problem with get-apt 
i have a proxy that's like proxy: ip  
and i think have edgy i guess.. this  i don't quite understand..

---

### Post by loclei on 2006-11-11
> **junglepeanut said:**
> Sorry I fell asleep. You still haven't explicitly said which version you are using, but I am going to assume it is dapper since you are trying to install that from one of the lines in your code. If that is the case, why are you making the symbolic link for sh, I am not sure it should effect anything but it does not make sense to me to do it as this was the link change I was talking about if you had edgy in my first post, not for dapper. Also if you do have Edgy first remember Edgy is a testing platform. Then instead of making a symbolic link change for sh do it with the links as posted here NOTE

NOTE NOTE This is for Edgy 
[http://www.marteydodoo.com/2006/08/29/installing-binary-ati-drivers-on-ubuntu-edgy/](http://www.marteydodoo.com/2006/08/29/installing-binary-ati-drivers-on-ubuntu-edgy/)

Second, it looks like you are not connected to the Internet in some fashion or apt is messed up as you are not able to even update.

i followed the commands and got to this :
```

user@user-desktop:~$ ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/edgy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/edgy
./packages/Ubuntu/ati-packager.sh: line 56: dpkg-architecture: command not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install

```
now what?

---

### Post by junglepeanut on 2006-11-11
Did you install Ubuntu LTS 6.06 this is called Dapper Drake (Stable Version), or 6.10 Edgy Eft (Testing Version), or Feisty Fawn even more unstable?

If you still do not know then there is a terminal command but I forget it. But you could check you source.lists and see if it is Dapper, or Edgy etc.

---

### Post by loclei on 2006-11-11
6.10
here's the name of the iso 

ubuntu-6.10-alternate-i386.iso

---

### Post by junglepeanut on 2006-11-11
Try doing it root, (mine always installs root) although it is complaining about wrong architecture what are your full system specifications? Especially processor.

---

### Post by loclei on 2006-11-11
cpu: 1.3 duron
ram: 512
video: radeon 9000 proII - 128mb

and you say i should login as root and do the same steps?

---

### Post by junglepeanut on 2006-11-11
I was getting ready and I got to thinking about how many different things you have wrong and I am wondering also if something else was chnaged which is making the other thins not work.

If you just did this install, it might be easier to start over as install only takes like 15 minutes (at least on my laptop) then you have a clean slate to start with the link I sent you. But it works mostly root only for me although it has worked sometimes when an older version was already installed with just sudo.
 

before reinstalling try the --listpkg command with the installer just to make sure you are using the right one, I know this is redundant but it would be nice to see what the installer thinks you should have since it is complaining.

---

### Post by loclei on 2006-11-11
--listpkg gives this:
```

user@user-desktop:~$ ./ati-driver-installer-8.28.8.run --listpkg
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
List of generatable packages:

Package Maintainer(s): Aric Cyr <acyr@gmail.com>
Status: Verified
Debian Packages:
        Debian/woody
        Debian/oldstable
        Debian/sarge
        Debian/stable
        Debian/sid
        Debian/unstable
        Debian/etch
        Debian/testing
        Debian/experimental

Package Maintainer(s): Niko Mirthes <nmirthes@gmail.com>
Status: Verified
Fedora Packages:
        Fedora/FC3
        Fedora/FC4
        Fedora/FC5
        Fedora/FC6
        Fedora/RHEL3
        Fedora/RHEL4

Package Maintainer(s): Arnaud Patard <apatard@mandriva.com>
Status: Verified
Mandriva Packages:
        Mandriva/2006
        Mandriva/2007

Package Maintainer(s): ATI
Status: Verified
RedHat Packages:
        RedHat/RHEL3_64a
        RedHat/RHEL3
        RedHat/RHEL4_64a
        RedHat/RHEL4

Package Maintainer(s): Stefan Dirsch <sdirsch@suse.de>
Status: Verified
SuSE Packages:
        SuSE/NLD9-AMD64
        SuSE/SLES9-AMD64
        SuSE/SUSE91-AMD64
        SuSE/NLD9-IA32
        SuSE/SLES9-IA32
        SuSE/SUSE91-IA32
        SuSE/SUSE100-AMD64
        SuSE/SUSE92-AMD64
        SuSE/SUSE93-AMD64
        SuSE/SUSE100-IA32
        SuSE/SUSE92-IA32
        SuSE/SUSE93-IA32
        SuSE/SLED10-AMD64
        SuSE/SLES10-AMD64
        SuSE/SUSE101-AMD64
        SuSE/SLED10-IA32
        SuSE/SLES10-IA32
        SuSE/SUSE101-IA32
        SuSE/SUSE102-AMD64
        SuSE/SUSE102-IA32

Package Maintainer(s): Aric Cyr <acyr@gmail.com>
Status: Verified
Ubuntu Packages:
        Ubuntu/warty
        Ubuntu/4.10
        Ubuntu/hoary
        Ubuntu/5.04
        Ubuntu/breezy
        Ubuntu/5.10
        Ubuntu/dapper
        Ubuntu/6.06
        Ubuntu/edgy
        Ubuntu/6.10

For example, to build a Debian Etch package, run the following:
% ./ati-driver-installer-<version>-<architecture>.run --buildpkg Debian/etch

Removing temporary directory: fglrx-install

```

---

### Post by msak007 on 2006-11-11
I still don't understand why you're trying to install the proprietary fglrx driver from ATI - it doesn't support your card any longer. Simply change the "Driver" line for your card in xorg.conf to "ati" or "radeon" to get 3D acceleration without any extra work.

---

### Post by junglepeanut on 2006-11-11
OK, I just saw this I need to go back and see if that is what it does as normally I just put in the right response, as I would have sworn it would only list ubuntu versions not all the others...

---

### Post by loclei on 2006-11-11
you mean to say that the 2.28.8 driver version doesn't support my radeon 9000 pro II?

---

### Post by junglepeanut on 2006-11-11
Missed msak007 response while typing. I was under the impression that he could not get even the open source as his Internet was boingo dud. And he had these downloaded already.

If you just want it to work and do have the ati open source installed already then msak007 is right. If not, your apt-get issues may make it pretty hard.

---

### Post by loclei on 2006-11-11
i had the ati open source drivers installed but then i removed them from the 
applications > add/remove

---

### Post by msak007 on 2006-11-11
> **loclei said:**
> you mean to say that the 2.28.8 driver version doesn't support my radeon 9000 pro II?
Sorry I didn't realize you were installing a previous version. Yes the **8.28.8** version was the last version that officially supported R200 cards.

Honestly when I first started using Ubuntu I was installing the drivers using the ATI script. Since then I've been using [this]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") guide (Method 2 to install the latest driver) and it has never failed me. According to Method 1, the 8.28.8 drivers you are trying to install manually are in the Edgy repos. If you just installed Edgy, I would follow the suggestion posted earlier to completely reformat again to start with a clean slate and follow that guide.

---

### Post by junglepeanut on 2006-11-11
The installer should work....

I do not know all of the changes you have made so the fact that it is not working is really confusing me as to what could be changed.

I think soon we are going to try back tracking all the way back to the beginning. Basically revert to original xorg.conf, see if this still works.
If it does then the drivers you need should still be installed. But we will still be left with the internet issue, I assume it is some type of proxy issue I have no experience with these but I have seen posts which say how to fix this, I have a funny feeling a huge part of this may be that when you try to do all of this your first error is you can not update as such you may not have the necessary dependencies to even install some of this. I could be wrong.

If we go all the way back and it works at least you can search and get your proxy thing figured out and then we can get some good results with drivers, hopefully. 

Last resort, it seems like you just did an install, and in eagerness have changed many things, my brother in law did this and is very far away, we first worked for 12 hours over im to fix it and I could not figure out what he did.

Then we reinstalled and he kept playing around and it stopped working but this time we were able to figure out exactly what his issue was because we knew all the old steps because when he made things that might be serious he wrote them down.

Hope we can figure this out.

---

### Post by loclei on 2006-11-11
so let's just try to start from the beggining
first - how to get rid of the drivers that i might have installed
second - how to revert to the first xorg.conf because i have several

---

### Post by loclei on 2006-11-11
i've followed this guide
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Installing_the_driver](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Installing_the_driver)
and i think i managed to install the driver afterall
```

user@user-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9000 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

user@user-desktop:~$ dmesg | grep fglrx
[17179611.080000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179611.084000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[17179611.084000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[17179616.620000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179616.620000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179616.620000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[17179616.620000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[17179616.636000] [fglrx] total      GART = 134217728
[17179616.636000] [fglrx] free       GART = 118222848
[17179616.636000] [fglrx] max single GART = 118222848
[17179616.636000] [fglrx] total      LFB  = 128970752
[17179616.636000] [fglrx] free       LFB  = 122679296
[17179616.636000] [fglrx] max single LFB  = 122679296
[17179616.636000] [fglrx] total      Inv  = 0
[17179616.636000] [fglrx] free       Inv  = 0
[17179616.636000] [fglrx] max single Inv  = 0
[17179616.636000] [fglrx] total      TIM  = 0
user@user-desktop:~$ 

```
and i've managed to run wow.exe with wine that's super
thx all for the support

---

### Post by junglepeanut on 2006-11-11
I actually don't know everything you have installed... I think the easiest way (for me as I am very new to Linux) to remedy this would be to actually do your steps in the opposite order as we could then use synaptic to visually see just the stuff that has to do with ati, I know there is a command line method but whenever I do it I get so much stuff it is hard to search through...then again I have a lot of stuff installed...

OK, 

cd /etc/X11/

then 

ls -l

and you should be able to see the dates and times for each xorg.conf
from this determine which is oldest, if you did not play with them, only packages did then this is probably the oldest but not guaranteed to be, so use the command above.=> xorg.conf.original-0

then you can make the back up of current anything you want

sudo mv xorg.conf xorg.confnotworkingyet

then 

sudo mv xorg.conf.original-0 xorg.conf

or instead of above commands you could open the xorg.conf.original-0
 file and save as xorg.conf since we know it doesn't work. Use your favorite terminal editor.

Then lets see how things work restart and post results.

Fingers crossed...

---

### Post by junglepeanut on 2006-11-11
OK cool, missed the post about it working, I thought your internet was pooched and that you had tried that already and it did not work. Glad it is working now, have fun.

---

### Post by loclei on 2006-11-11
thx but since i managed to run wow with wine i think i have the drivers installed :)
thx for everything

---

