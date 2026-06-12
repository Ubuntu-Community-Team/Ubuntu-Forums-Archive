---
title: "nVidia driver installation"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by gshyland on 2007-08-29
Hi, I'm a total linux newbie :) ...but I've been around since DOS days.

I just got Ubuntu installed on my PC, dual-booting with WinXP, and I was pretty happy how painless the basic installation was. I just downloaded and burned the live CD, set up some partitions, went through the install, went through a couple hundred megs of updates, and I was up.

But now I'm trying to install nVidia graphics card drivers, and I've encountered my first hurdle. (I need 1280x1024 for my LCD monitor, and I plan to be using some 3D games as well.)

I downloaded "NVIDIA-Linux-x86-100.14.11-pkg1.run" from nVidia , and ran it per the instructions on their site.  It unpackaged all the files, then gave me a message something like "<this program> must be run as root."

As I recall from way back, "root" is the superuser, correct? 
I get the impression I need to be logged in as "root".
I can't login as root, or admin. I didn't notice any step setting up accounts, other than the ones I imported from WinXP, during the installation from the live CD. I checked again, booting from the live CD and going through the installation dialogs without really installing.

What'd I miss? How do I get logged in with the rights to install drivers?

---

### Post by forestpixie on 2007-08-29
when you run the instructions in terminal 

putting sudo before the command they've specified will run it as root

---

### Post by Seti on 2007-08-29
Don't do it that way. If you've installed Feisty Fawn, all you need to do is go to:
>System>Administration>Restricted Drivers Manager
and enable it. You will be required to enter YOUR password, because by default (since YOU did the installation) you have the right to use sudo. It will then download the driver and install it. Reboot your comp, and voila!

Good luck!

---

### Post by FuturePilot on 2007-08-29
You're going to need all the development packages installed so that it can build the kernel module. Or it might be easier if you do System>Administration>Restricted Drivers Manager and install it that way.

---

### Post by gshyland on 2007-08-29
Thanks! Trying it. :)

---

### Post by steve.horsley on 2007-08-29
This is not the best way to install software at all. Ubuntu has huge repositories of software  that's already built/compiled especially for Ubuntu, and you should always look there first.

Menu System->Administration->Software Sources and make sure the Multiverse and Universt repositories are enabled. You will need to reload the software catalogs after making this change (it prompts you to do so). Then System->Administration->Synaptic, and search for and install the package nvidia-glx-new. That should do the trick for you.

EDIT: I type too slow, don't I. And they're right - the Restricted Drivers thingy is another way to go, but it gets you to the same place - drivers from the repos, already made specially for this particular version of Ubuntu, and you can be sure that any security updates that change the kernel will coma with an updated driver to match.

---

### Post by Seti on 2007-08-29
> **steve.horsley said:**
> This is not the best way to install software at all. Ubuntu has huge repositories of software  that's already built/compiled especially for Ubuntu, and you should always look there first.

Menu System->Administration->Software Sources and make sure the Multiverse and Universt repositories are enabled. You will need to reload the software catalogs after making this change (it prompts you to do so). Then System->Administration->Synaptic, and search for and install the package nvidia-glx-new. That should do the trick for you.

Not at all necessary if he's using Feisty, IIRC. Multiverse and Universe are already included with this release.

---

### Post by cubeist on 2007-08-29
And just a short clarifications... you should almost never need to log in as the root user.  If you aren't exactly sure of what you are doing as root you could severely damage your system.  For most (99%) of tasks you will just need to enter your system password.  For example, when starting the Synaptic Package Manager (System/Synaptic Package Manager) it will ask for your system password.  Also, sometimes when you are executing commands via the terminal you will need to start with "sudo" which will execute the command with SuperUser privileges but does not enable root access.  It's just temporary higher authority access.

Cheers

---

### Post by Perfect Storm on 2007-08-29
As other have said, best to use the nvidia driver you can find in synaptic package manager.


But if you are adventurous and want to wrestle with commands;

Download the driver to your Desktop, then to the terminal;

```
sudo nano /etc/default/linux-restricted-modules-common
```

change **DISABLED_MODULES=""** to **DISABLED_MODULES="nv"**

```
cd ~/Desktop
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-XXXX-pkg1.run
sudo /etc/init.d/gdm start
```

Note that gdm stop command will take you out of X and you'll be in CLI only.

---

### Post by toolsheded on 2007-09-01
> **Seti said:**
> Don't do it that way. If you've installed Feisty Fawn, all you need to do is go to:
>System>Administration>Restricted Drivers Manager
and enable it. You will be required to enter YOUR password, because by default (since YOU did the installation) you have the right to use sudo. It will then download the driver and install it. Reboot your comp, and voila!

Good luck!

I was reading through the forums right after I had installed ubuntu 7. I was having some trouble getting my video card installed,so I followed these directions. After reboot, all I get is a blank screen. In fact, I get no screen. The monitor turns off as soon as I get past the GRUB screen and then doesn't turn back on. BTW the video card in question is an NVIDIA 8800GTS. It was working before I enabled the restricted driver from NVIDIA. Any suggestions where I go now?

---

