---
title: "So I don't know what I am doing"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by incogn(egro)ito on 2008-02-23
So I finally got my PC built and decided to install Ubuntu. Didn't take too long getting my wireless card working, but now I am trying to get my video card working (8800GTX). From what I read people had a lot easier time installing the ubuntu created drivers rather than the Nvidia ones. So I decided to go that route, I have been installing package after package and finally when I thought I made it. A the package nvida-glx which is a supposed dependency of nvidia-glx-new is conflicting with it and nvidia-glx-new will not install without it. So can someone help me ;(

---

### Post by Presto123 on 2008-02-23
Okay...uninstall everything and go with JUST the -new one.

---

### Post by Yoke &amp; Chung on 2008-02-23
I couldn't get my 8600GTS working using the restricted driver too, so in the end I downloaded the latest Linux driver from nVidia and it is working fine now.

---

### Post by Presto123 on 2008-02-23
Okay. Glad you got it working. :)

---

### Post by mgranet on 2008-02-23
That won't help. The 8800 series aren't supported by the drivers in the repos. You can either download them from Nvidia, or use Envy. I suggest the latter.

---

### Post by toa on 2008-02-23
so the issue is [SOLVED]

---

### Post by incogn(egro)ito on 2008-02-23
I am trying to install the Ubuntu one's and well I am failing miserably, because somehow a dependency is conflicting with nvidia-glx-new.

Few seem to have success with the nvidia driver, so I was wondering if there is some sort of work around or am I seriously missing something. Because everytime I uninstall nvidia-glx and attempt to install nvidia-glx-new it says nvidia-glx is a dependency, but when  I have it installed nvidia-glx-new will not install because nvidia-glx is conflicting with it.

---

### Post by incogn(egro)ito on 2008-02-23
> **mgranet said:**
> That won't help. The 8800 series aren't supported by the drivers in the repos. You can either download them from Nvidia, or use Envy. I suggest the latter.
I tried using Envy and I am getting Error: Dependency is not satisfiable: Libstdc++5. I am apparently running a new version ofLibstdc++5.

---

### Post by mgranet on 2008-02-23
> **incogn(egro)ito said:**
> I am trying to install the Ubuntu one's and well I am failing miserably, because somehow a dependency is conflicting with nvidia-glx-new.

Few seem to have success with the nvidia driver, so I was wondering if there is some sort of work around or am I seriously missing something. Because everytime I uninstall nvidia-glx and attempt to install nvidia-glx-new it says nvidia-glx is a dependency, but when  I have it installed nvidia-glx-new will not install because nvidia-glx is conflicting with it.

You can't use ANY of the drivers in the repos. They are too old to work with the 8800 series. You should remove both of them, install the build-essential package, as well as the kernel headers, and download and install the drivers from the Nvidia site.

---

### Post by Fred_E _krugar on 2008-02-23
Just go here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 

Install it and then run, and let it install the drivers for you.

---

### Post by mgranet on 2008-02-23
> **incogn(egro)ito said:**
> I tried using Envy and I am getting Error: Dependency is not satisfiable: Libstdc++5. I am apparently running a new version ofLibstdc++5.

Ahh, dependency hell. It happens. I'm sure there are workarounds, but you are probably best getting Nvidia's drivers. :)

---

### Post by Fred_E _krugar on 2008-02-23
try installing build-essentials

---

### Post by incogn(egro)ito on 2008-02-23
I installed the build essentials, I think.

sudo apt-get instal build essential and it seems to have ran find. I still get the same error though. And it seems like I am the first in the universe with this problem ;_; google and nothing here has been able to help me. I have been reading other threads with no luck.

---

### Post by mgranet on 2008-02-23
8800 problem or Envy problem? You have a dependency issue with envy, the only way I can think of to correct that would be to locate the correct version of libstdc++5, and downgrade. I really think you are much better off downloading the kernel headers and Nvidia drivers and going that route. As long as you make sure you remove all the currently installed nvidia drivers, the installation should be pretty painless.

The woman just told me I'm past curfew, so I'll do a quick rundown before I'm off:
Download/install linux-headers 2.6.22-14 from the repos
Download nvidia drivers from nvidia.com
Log off
From the drop down menu, select Console Login.
Log in
cd to the dir where you stored the driver, and
sudo sh NVIDIA-Linux-x86-169.09.pkg1.run
It will ask you if it can search for kernel modules. I don't think it will find any, it will probably have to build them. Let it.
Do whatever else it says (I don't think there are any other steps, but it's late)
Reboot
If it returns to a console login on reboot, login then type startx
If that fails, you may need to do a sudo dpkg-reconfigure -phigh xserver-xorg
you may also need to edit your xorg.conf (in /etc/X11) to include your preferred resolution.

---

### Post by incogn(egro)ito on 2008-02-23
Says I need to exit X server before I install. How do I go about doing that? I figured out how to actually turn off xserve and have tried to run the driver over 3 times with no luck. I followed your directions and Ubuntu still can not find or recognize the driver.

----- 
This can be closed as solve with the help of mgranet a few other threads and a whole lot of me just reattempting and re-reading :). Also the nvidia site gives terrible directions.

---

### Post by mgranet on 2008-02-24
Just for anyone who reads this; what they mean by exiting the Xserver is by logging into the console. (Select "console login' from the drop down menu of the X login screen). 
Also, instead of sudo sh nvidia-driverver.sh, it should be a '.run'. Finished code for current drivers would be:
sudo sh NVIDIA-Linux-x86-169.09.pkg1.run

---

