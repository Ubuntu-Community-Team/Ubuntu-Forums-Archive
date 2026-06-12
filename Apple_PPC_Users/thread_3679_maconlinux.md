---
title: "maconlinux"
date: 2004-11-08
forum: Apple PPC Users
---

### Post by trash on 2004-11-08
Has anybody tried this?

MOL has been packaged for Debian, so you can simply install it via your favorite tool. If you want to try the most recent version on a system running stable (woody), add the line

    deb [http://people.debian.org/~jensen](http://people.debian.org/~jensen) woody/

to your /etc/apt/sources.list file.


UPDATE:
here's what i got so far and it's lookin good... won't get a chance to finish setting it up for a few days though... 
*******************
# apt-get install mol
Reading Package Lists... Done
Building Dependency Tree... Done
The following extra packages will be installed:
  mol-drivers-linux mol-modules-2.2.20
Suggested packages:
  kernel-image-2.2.20 kernel-image-2.2.20-pmac
The following NEW packages will be installed:
  mol mol-drivers-linux mol-modules-2.2.20
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1103kB of archives.
After unpacking 3756kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe mol-drivers-linux 0.9.70+1-1 [45.1kB]
Get:2 [http://people.debian.org](http://people.debian.org) woody/ mol-modules-2.2.20 0.9.68+20030312-1 [67.9kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe mol 0.9.70-6 [990kB]
Fetched 1103kB in 3m29s (5255B/s)

Preconfiguring packages ...
Selecting previously deselected package mol-drivers-linux.
(Reading database ... 60317 files and directories currently installed.)
Unpacking mol-drivers-linux (from .../mol-drivers-linux_0.9.70+1-1_powerpc.deb) ...
Selecting previously deselected package mol-modules-2.2.20.
Unpacking mol-modules-2.2.20 (from .../mol-modules-2.2.20_0.9.68+20030312-1_powerpc.deb) ...
Selecting previously deselected package mol.
Unpacking mol (from .../mol_0.9.70-6_powerpc.deb) ...
Setting up mol-modules-2.2.20 (0.9.68+20030312-1) ...

Setting up mol-drivers-linux (0.9.70+1-1) ...
Setting up mol (0.9.70-6) ...
*************************

rebooted and then i tried:

as root... 'startmol --loadonly' and got.... 
*************************************************************
 No video modes have been configured. Please run 'molvconfig'
 as root to configure full screen video or disable console
 video in /etc/mol/molrc.video.
*************************************************************

so i'm felling confident but we'll see:)

---

### Post by TekMate on 2004-11-08
Let us know how it works I don't use it much myself but it definately comes in handy.

---

### Post by trash on 2004-11-08
just realized i need to compile mol.. and i have yet to compile anything successfully lol.
The instructions seem simple enough, but then again they always do... back at it in a few days i think. I'll post the results for sure:)

---

### Post by Down8ve on 2004-11-14
I was able to get the molvideoconfig settings done, but even after following the instructions from the Ubuntu Wiki it says there is a version mismatch even though the numbers are the same.

Say, Xfce is pretty nice!

Scott

---

### Post by trash on 2004-11-15
did you try the howto on the mol website?

Frankly Ubuntu is pretty complete as is as far as apps that work... and after exploring it a bit more i'm starting to wonder if i really need mol at all... being rather low tech to start with it could be just one less headache for me to deal with lol.
I'll get on it again soon.

but judging by the numbers of people viewing the thread it is clear this needs working on

---

### Post by [paZx] on 2004-11-21
Hi to all people.
I'm sorry for my poor english, i will do my best to to write in a correct english 

I want install mol tu use Phanter, but i need install kernel source too.
This i smy problem:

drei@ubuntu:/usr/src $ sudo uname -a
Linux ubuntu 2.6.8.1-3-powerpc #1 Tue Oct 12 13:15:29 BST 2004 ppc GNU/Linux

drei@ubuntu:/usr/src $ sudo apt-get -s install kernel-source
......
  kernel-source-2.6.7 2.6.7-3ubuntu2
  kernel-source-2.6.6 2.6.6-2
  kernel-source-2.6.5 2.6.5-4
  kernel-source-2.4.26 2.4.26-6
  kernel-source-2.4.25 2.4.25-3
  kernel-source-2.4.24 2.4.24-3
  kernel-source-2.2.25 2.2.25-3
......


there'is not my kernel source!
Someone know where can i find them?
Thank a lot

---

### Post by stereo on 2004-11-24
it's not kernel-source... it's linux-source to get the ubuntu-linux

---

### Post by Ptero-4 on 2004-12-06
[QUOTE=stereo]it's not kernel-source... it's linux-source to get the ubuntu-linux[/QUOTE]
 Hi, have you been able to build maconlinux. I followed the instructions on the Ubuntu Wiki but it fails with an `unconfigured kernel` error and I can´t build it. Is there any thing (besides the setup.h modification which I already did) that you needed to do that isn´t pointed out in the Wiki?

---

### Post by val1984 on 2004-12-06
You need linux-headers to compile mol-modules but not linux-source...

---

### Post by Ptero-4 on 2004-12-07
[QUOTE=val1984]You need linux-headers to compile mol-modules but not linux-source...[/QUOTE]
 Hi. I got it working. I pulled the mol-kmods from Mandrake 10.1 rc1 ppc and packed them as a tar.bz2 (alien coulnd´t deb them out). You have to install first mol, mol-drivers-linux, mol-drivers-macos, mol-drivers-macosx, and mol-modules (not mol-modules-source). Then as root you have to copy or move the mol-kmods archive to /usr/lib/mol and unpack it. Then as root run dpkg-statoverride --update --add root root 4755 /usr/lib/mol/bin/mol. After doing that mol will be ready to run and you will only need to configure it.

note: if it complains about not being able to find the modules make sure that the modules are in /usr/lib/mol/modules and not in /usr/lib/mol/modules/modules or some other odd path and if you have kernel 2.6.8.1-3-powerpc and it fails change it to 2.6.8-powerpc (both kernels are installed by default, you just need to point the vmlinux and initrd.img symlinks to vmlinux-2.6.8-powerp and initrd.img-2.6.8-powerpc and reboot).

---

### Post by val1984 on 2004-12-07
There's an How-To in Ubuntu Wiki :
[http://www.ubuntulinux.org/wiki/MacOnLinuxHowto/](http://www.ubuntulinux.org/wiki/MacOnLinuxHowto/)

---

### Post by J_Sine on 2004-12-08
My first go-round with MOL I used all of the 2.6.8 packages I found listed in Synapytic. Worked without
issue as far as MOL was concerned, but then my Linux-wlan-ng wireless modules needed to be
rebuilt for the new kernel. Not to mention I was getting all sorts of extraneous data on boot-up.
So I ended up switching my yaboot back to the standard 2.6.8.1-3 kernel and followed the wiki
to build MOL kernel modules form my current kernel. After a little frustration I realized I had
downloaded all the needed files except the "build-essential" package (as stated in the wiki! Doh!)
Once I installed that, the MOL kernel modules built, packaged and installed without issue and MOL
has been running fine ever since! I must say it again,  the combination of Ubuntu with the linux-wlan
modules already working, a custom install of KDE and now OS 10.3.6 via MOL, I have the 
best of both worlds without having to reboot. Now if only I could get Bochs configured, I'd be all set.
 :mrgreen:

---

### Post by SyL on 2004-12-15
Hi,
 
  I followed the wiki's howto and that work normally. 
 The only problem is that molvconfig can't find any resolution working in 15 or 24 depths. Only the 8 depths works. But with a 8 depth configuration the display is really disgusting.
 I try to modify /var/lib/mol/fb_modes  by hand, the display change into a more disgusting screen and I got the following error :
  ```
Unimplemented store instruction 7E4019CE
``` 
 
 Anybody have a idea ?

---

### Post by val1984 on 2004-12-15
I had no problems with molvconfig, that's quite weird you had some :/

---

### Post by SyL on 2004-12-16
[QUOTE=val1984]I had no problems with molvconfig, that's quite weird you had some :/[/QUOTE] 
 
 I think that the problem must certainly come from my graphics card.

---

### Post by pdaliu on 2004-12-24
[QUOTE=SyL]Hi,
 
  I followed the wiki's howto and that work normally. 
 The only problem is that molvconfig can't find any resolution working in 15 or 24 depths. Only the 8 depths works. But with a 8 depth configuration the display is really disgusting.
 I try to modify /var/lib/mol/fb_modes  by hand, the display change into a more disgusting screen and I got the following error :
  ```
Unimplemented store instruction 7E4019CE
``` 
 
 Anybody have a idea ?[/QUOTE]

Hi:
  I also have this low-resolution problem.  What's your graphics card?  Mine is NVidia GeForce2 MX 32MB along with G4.  Thanks!

---

### Post by SyL on 2004-12-26
[QUOTE=pdaliu]Hi:
 I also have this low-resolution problem. What's your graphics card? Mine is NVidia GeForce2 MX 32MB along with G4. Thanks![/QUOTE] 
 Yes, this is a GeForce FX Go5200 32M on PB 12" G4
 There is some body who can give us a   /var/lib/mol/fb_modes  working with all depths  on 12" (1024*768 60Hz) ? 
 just for try, it will be great!
 
 Thanks!

---

### Post by matsie on 2008-03-27
It seems as if the repository [http://people.debian.org/~jensen](http://people.debian.org/~jensen) woody/ is not working any more. Is there any other repository?

---

