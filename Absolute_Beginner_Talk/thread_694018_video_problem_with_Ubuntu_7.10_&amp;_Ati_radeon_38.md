---
title: "video problem with Ubuntu 7.10 &amp; Ati radeon 3870"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by mawwam on 2008-02-11
Hi I'm new to Ubuntu and linux at all. My videocard is Ati Radeon 3870. Ubuntu don't recognize it and every time loads graphics in low res mode. I tried to lunch restricted driver manager - it said "you don't need restricted driver manager" or something like that. 

I found 2 different links how to install the drivers: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Instalation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Instalation_Guide) and one other /I don't remember the link/. The first want me to enable restricted repository and I wrote in the terminal /etc/apt/sources.list but I got "bash: /etc/apt/sources.list: Permission denied" 
The second link uses Ati 8.443.1 driver /The first is from official site of ATI and the driver is 8.01/ However I couldn't download nor of them because: "E: Couldn't find package ati-driver-installer...."

So I'm in kinda dead end. Help me with ideas please.

---

### Post by xc3RnbFO8P on 2008-02-11
> [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

or you could try to install Envy:
> 
[http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb)

---

### Post by mawwam on 2008-02-11
OK - you gave mi the second link from my post  but i got this:
 apt-get install ati-driver-installer-8.443.1-x86.x86_64.run
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ati-driver-installer-8.443.1-x86.x86_64.run

So I couldn't execute step 2:
./ati-driver-installer-8.443.1-x86.x86_64.run --buildpkg Ubuntu/gutsy
bash: ./ati-driver-installer-8.443.1-x86.x86_64.run: No such file or directory

I installed the envy but nothing happened - is there something special about running the drivers in it?

---

### Post by xc3RnbFO8P on 2008-02-11
Read this:
> 
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

---

### Post by mawwam on 2008-02-11
Thank you very much!!! I was on the edge to give up from linux, but now I will really enjoy learning how to use it :)

---

### Post by xc3RnbFO8P on 2008-02-11
Glad to help.

---

### Post by Páraquedas_cascais on 2008-02-13
Hi, :confused: didn't work to me! i'm new in linux

I tried to install like -> [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)  and ops... black screen... :lolflag:, then i tried to go safe mode and to recover i did the "sudo cp xorg_original-0.conf xorg.conf " then :lolflag: reboot and i back in ubuntu...enormous 800*600 vesa,  well next i read about Envy...

I tried Envy, now i have a white screen... and it's freeze nothing moves even the hourglass... (tried 3 times, last ATI driver download )

So can you help me? :confused:  We can try this online at night :popcorn: it's fun, install uninstall, install again :lolflag: this is my 2º week now :lolflag: 

Edit:
fglrxinfo   <- gives me an error display ??


By the way my system it's new:
P5E
G-SKILL PC8000 4G
Q6600
Asus ATI EAH3870 
SEAGATE 250G 16M SATAII
SAMSUNG 2032BW


PS: i'm trying to leave Windows, give them a RIP, but it's complicated

---

### Post by Páraquedas_cascais on 2008-02-13
don't let this die!!! HELP

---

### Post by Páraquedas_cascais on 2008-02-13
Hello!

](*,)](*,)

HELLLLLLLLLLLLPPPPPPPPPPPPPPPPPPPPPP!!!!

---

### Post by onegreenparker on 2008-02-13
[This]("http://ubuntuforums.org/showthread.php?t=499060&highlight=6715s") helped me

Follow the instructions posted by srd

---

### Post by tseliot on 2008-02-13
> **Páraquedas_cascais said:**
> Edit:
fglrxinfo   <- gives me an error display ??


By the way my system it's new:
P5E
G-SKILL PC8000 4G
Q6600
Asus ATI EAH3870 
SEAGATE 250G 16M SATAII
SAMSUNG 2032BW


PS: i'm trying to leave Windows, give them a RIP, but it's complicated

You're graphic card is not (yet) supported by the ATI driver on Linux.

---

### Post by Páraquedas_cascais on 2008-02-13
new driver ATI 8.2 :confused:

---

### Post by Páraquedas_cascais on 2008-02-13
hi again making progress here!  But need help...

> bcascais@Bruno-ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

bcascais@Bruno-ubuntu:~$ ls
ASUS-ATI_GRAFIC  Documents  file:  nautilus-debug-log.txt  Public     Videos
Desktop          Examples   Music  Pictures                Templates
bcascais@Bruno-ubuntu:~$ cd ASUS-ATI_GRAFIC
bcascais@Bruno-ubuntu:~/ASUS-ATI_GRAFIC$ LS
bash: LS: command not found
bcascais@Bruno-ubuntu:~/ASUS-ATI_GRAFIC$ ls
ati-driver-installer-8-02-x86.x86_64.run
fglrx-amdcccle_8.455.2-0ubuntu1_amd64.deb
fglrx-installer_8.455.2-0ubuntu1_amd64.changes
fglrx-kernel-source_8.455.2-0ubuntu1_amd64.deb
xorg-driver-fglrx_8.455.2-0ubuntu1_amd64.deb
xorg-driver-fglrx-dev_8.455.2-0ubuntu1_amd64.deb
bcascais@Bruno-ubuntu:~/ASUS-ATI_GRAFIC$ sudo dpkg -i fglrx-amdcccle_8.455.2-0ubuntu1_amd64.deb
[sudo] password for bcascais:
Selecting previously deselected package fglrx-amdcccle.
(Reading database ... 92790 files and directories currently installed.)
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.455.2-0ubuntu1_amd64.deb) ...
Setting up fglrx-amdcccle (8.455.2-0ubuntu1) ...

bcascais@Bruno-ubuntu:~/ASUS-ATI_GRAFIC$ 

MESA????? Now what? It would have to be ATI Radeon HD 3870 !!!

Help!! i'm getting there!

Buy the way ... after installing xorg-driver-fglrx  a checking error occurred "Couldn't verify integrity of fglrx"  i think i have too many installation already..
What can i do about that and about Mesa?
The Catalysm application doesn't work ether!

---

### Post by Páraquedas_cascais on 2008-02-14
Try to change xorg.conf, device = fglrx   but didn't work.

How can i remove all fglrx instalation

---

### Post by an4rew on 2008-03-08
any easy fixes for noobs yet?

---

### Post by Nimra on 2008-04-29
Okay. First I'd uninstall the fglrx driver so open a terminal and type:

/usr/share/ati/fglrx-uninstall.sh

then get the new ATI driver

wget [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-4-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-4-x86.x86_64.run)

this will download the driver to the folder you are

then change the permissions that you can run the installer

chmod +x ./ati-driver-installer-8-4-x86.x86_64.run

then you should install some packages:

sudo apt-get update && sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)

then you can run the installer:

sudo sh ./ati-driver-installer-8-4-x86.x86_64.run

then follow the instructions of the installer

if you have done all this you should edit your /etc/X11/xorg.conf (if you haven't already done that)

then reboot your pc and type glxinfo|grep direct in a terminal. Then it should say
direct rendering: Yes
if it does not you could have to edit your /etc/default/linux-restricted-modules-common and insert fglrx to the disabled modules. it should look like this:
DISABLED_MODULES="fglrx"
then reboot and that's it

---

### Post by PoopyTheJ on 2008-05-01
Nimra you said then you should edit your xorg file if you haven't done so, though I know how to get to and edit the xorg file, I have no idea what I should edit it to say, what do I edit it to say?

---

### Post by Nimra on 2008-05-01
you have to go to the section "Device" and change the "driver" to fglrx. It should look like this:

Section "Device"
	Identifier  "RadeonHD3870"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

(or similar)

---

