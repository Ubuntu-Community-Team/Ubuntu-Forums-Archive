---
title: "NVIDIA Linux Display Driver - x86 Installation Guide for ubuntu 7.10 Users"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by eewujian on 2008-02-01
Hello everyone,
I'm an absolute newbie to linux.It took me nearly a month to figure out how to install the NVIDIA driver on my system. I summarized the steps here.
Jian

1) Download NVIDIA display driver from [www.nvidia.com](www.nvidia.com)
NVIDIA-Linux-x86-169.09.pkg1.run

2) Install packages:
linux-kernel-devel
pkg-config
xserver-xorg-dev

3) Uninstall packages:
nvidia-glx
linux-restricted-modules
linux-restricted-modules-common

4) Delete files (if exist):
/etc/init.d/nvidia-glx
/etc/init.d/nvidia-kernel
/lib/linux-restricted-modules/.nvidia_new_installed

5) Exit X
sudo /etc/init.d/gdm stop
Press "Ctrl+Alt+F1"
log in

6) Install NVIDIA display driver
sudo sh NVIDIA-Linux-x86-169.09.pkg1.run
(Follow instructions to compile the NVIDIA kernal interface)

7) Restart X
sudo /etc/init.d/gdm restart

8) Create customized X server configuration file (optional)
a) sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
b) Go to "Applications->System Tools->NVIDIA X Server Settings->X Server Display Configuration" and customize settings (to anything you want).
c) Click "Save to X Configuration"
d) Uncheck "Merge with existing file."
e) Click "Show preview..."
f) Open another terminal and type "sudo gedit /etc/X11/xorg.conf"
g) Replace the content in the opened file by the content in the window that h) opened by clicking "Show preview...".
i) Save the file.
j) Exit X
k) Restart X

---

### Post by Nythain on 2008-02-01
and ill be one of the first to point out...
This will need to be done EVERY time you update your Kernel... i dont know how many people install this way (wich isnt to bad because its a way to keep up to date on drivers, the repo ones tend to get a bit outdated) and then post, "Kernel update broke my ubuntu" because no one bothered to mention that they are gonna have to do this after every kernel upgrade

---

### Post by jaytek13 on 2008-02-01
Well, that's certainly the long route and could be useful, but may I ask why you did that instead of just using the restricted drivers manager?

---

### Post by JoshuaRL on 2008-02-01
> **Nythain said:**
> and ill be one of the first to point out...
This will need to be done EVERY time you update your Kernel... i dont know how many people install this way (wich isnt to bad because its a way to keep up to date on drivers, the repo ones tend to get a bit outdated) and then post, "Kernel update broke my ubuntu" because no one bothered to mention that they are gonna have to do this after every kernel upgrade

That's a great point.  Which also explains why you need to reinstall all that when you upgrade, since it's also a new kernal.

---

### Post by Shazaam on 2008-02-02
Instead of uninstalling linux-restricted-modules it's better to edit /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy)--

    DISABLED_MODULES="nv nvidia_new"

per...[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

---

### Post by dcstar on 2008-02-02
> **Nythain said:**
> and ill be one of the first to point out...
This will need to be done EVERY time you update your Kernel... i dont know how many people install this way **(wich isnt to bad because its a way to keep up to date on drivers, the repo ones tend to get a bit outdate**d) and then post, "Kernel update broke my ubuntu" because no one bothered to mention that they are gonna have to do this after every kernel upgrade

Unless you are running very new hardware or have a specific issue that the drivers in the repository can't fix, I see no need whatsoever to muck around manually installing drivers from the Nvidia site.

How many people (who don't yet know better) are going to read threads like this and unnecessarily get themselves into trouble by installing new drivers on their already perfectly working systems?

---

### Post by Nythain on 2008-02-02
Well, i didnt really start the thread, just threw my two cents in.
As far as newer drivers, there's tons of good reasons to have the most up to date drivers, i mean, they're released for a reason, sometimes they add new functionality, sometimes they fix known problems.
I personally just use nvidia-glx-new, but thats besides the point... my only main point was warning users who read this thread and follow those instructions, that it will need to be repeated if/when they update thier kernel.

on a side note... if you follow those directions, you really shouldnt encounter any problems... i mean, they are pretty straight forward, and before all the improvements in driver installation and compatability and whatnot over the years and versions of ubuntu, those were pretty much the exact same steps i followed.

and sometimes a default install of ubuntu isnt a "perfectly working system"
Once again, i dont condone the manual installation of drivers, but i cant see a reason not to if you really want bleeding edge drivers (wich there is reason for believe it or not)

---

### Post by ThePinkWitch on 2008-02-02
Thanks for the info on this subject. I downloaded the NVIDIA drivers and burnt them onto a CD because the machine with Ubuntu isn't on the net yet, and I can't get the drivers to install off the CD. I tried typing in the terminal but no go and the restricted device thingy won't enable the drivers either. I have a really old nvidia graphics card so guess thats the problem. Nvidia Geforce GTS GeForce Pro (32mg).

---

### Post by eewujian on 2008-02-02
> **dcstar said:**
> Unless you are running very new hardware or have a specific issue that the drivers in the repository can't fix, I see no need whatsoever to muck around manually installing drivers from the Nvidia site.

How many people (who don't yet know better) are going to read threads like this and unnecessarily get themselves into trouble by installing new drivers on their already perfectly working systems?

Thanks for the advice.
Here is my reasons.

1) I have a NVIDIA GeForce 8600GT card and I could not find a generic NVIDIA driver for it that support dual monitors.
2) I'm going to install CUDA for graphics card-based programming, which requires the proprietary driver provided by NVIDIA.

Jian

---

### Post by dcstar on 2008-02-02
> **ThePinkWitch said:**
> Thanks for the info on this subject. I downloaded the NVIDIA drivers and burnt them onto a CD because the machine with Ubuntu isn't on the net yet, and I can't get the drivers to install off the CD. I tried typing in the terminal but no go and the restricted device thingy won't enable the drivers either. I have a really old nvidia graphics card so guess thats the problem. Nvidia Geforce GTS GeForce Pro (32mg).

The older Nvidia cards require the** nvidia-legacy** package (and the dependencies), there are posts in the forums on how to get packages on one PC with 'net access and transfer them to another without 'net access.

---

### Post by aNaLpLeAsEr on 2008-02-15
Hello people
I am also new to Linux and Ubuntu. I am having difficulties with installing nvidia drivers so i can use dual display. Unfortunetly the above guide hasn't helped me,

Please can someone help me? Remember I am a beginner!!!!!

---

### Post by kpkeerthi on 2008-02-15
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by aNaLpLeAsEr on 2008-02-15
thanks for reply.

gone to Restricted drivers and clicked on enabled box for the NVIDIA accelerated graphics driver and get a pop up to verify the process. I then get this message

   The software source for the package

   nvidia-glx-new

   is not enabled.


This is the second PC i have installed Ubuntu on. the first one, an older computer with a Matrox g550 card just would not work with Ubuntu or my wireless USB adapter. I searched these forums and the net via google and it would seem I was unlucky with my old hardware selection. As you can imagine im getting very disheartened by all the hassle. I cant even add applications with ubuntu and this PC i get a message "the list of applications is unavailable". I hit reload and it appears to download something but the same message comes up when i try again?!?

Please tell me Im just unlucky and that the Linux world isn't really like this.

---

### Post by kpkeerthi on 2008-02-18
> The software source for the package

nvidia-glx-new

is not enabled.

Go to System -> Administration -> Software Sources and enable **universe and multiverse **repositories.

---

