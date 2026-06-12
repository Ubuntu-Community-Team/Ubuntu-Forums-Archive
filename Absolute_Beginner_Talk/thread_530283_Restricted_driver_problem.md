---
title: "Restricted driver problem"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by kv_abhiram on 2007-08-20
Hi, I recently installed Ubuntu in my system which has an Nvidia Graphics Card ( 5500) agp card and I am not able to enable the restricted driver in it. It is asking me to download the Nvidia drivers from the website

but currently im not able to connect to internet either coz  theres some problem with my internal modem

i also have an windows-Xp installed in parallel hard drive.. through which i can access the internet

---

### Post by Hobo Joe on 2007-08-20
Download [this]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run") file first.(Not if your running 64-bit though)
And then run the command:
```

sh NVIDIA-Linux-x86-100.14.11-pkg1.run

```
It will be a guided installer that will  ask you a few questions.

EDIT:

I just realized that you don't have internet access on your computer, so I need to add to this.

When you download the file, put it right on the desktop, and then BEFORE you run the command above, type:
```

cd Desktop

```

---

### Post by igknighted on 2007-08-20
> **kv_abhiram said:**
> Hi, I recently installed Ubuntu in my system which has an Nvidia Graphics Card ( 5500) agp card and I am not able to enable the restricted driver in it. It is asking me to download the Nvidia drivers from the website

but currently im not able to connect to internet either coz  theres some problem with my internal modem

i also have an windows-Xp installed in parallel hard drive.. through which i can access the internet

Restricted driver manager needs to go online to install the drivers.  To do it yourself is really easy though.  Just go to packages.ubuntu.com, then browse to the folder with your release and architecture and download the package 'nvidia-glx' and the proper 'kmod' package for your kernel (run the command 'uname -a' to find this info).  I don't remember the exact naming scheme for the kmod, probably kmod-nvidia-glx-2.6.21-15.1386.deb or something like that.

Once you have downloaded these from windows, switch to linux and make sure those files are on media you can read (flash drive, shared partition, anything) and install them.  You might need to manually enable them, so post back if you have more issues.

---

### Post by igknighted on 2007-08-20
> **Hobo Joe said:**
> Download [this]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run") file first.(Not if your running 64-bit though)
And then run the command:
```

sh NVIDIA-Linux-x86-100.14.11-pkg1.run

```
It will be a guided installer that will  ask you a few questions.

This method will not work because (a) you need to disable GDM and the graphical server first, and (b) you would need to download and install the kernel headers and the compiler tools before this could run.  It is easiest just to install the packages from the repos.

---

### Post by Hobo Joe on 2007-08-20
> **igknighted said:**
> This method will not work because (a) you need to disable GDM and the graphical server first, and (b) you would need to download and install the kernel headers and the compiler tools before this could run.  It is easiest just to install the packages from the repos.

Oh jeez, I forgot all about that! Ah well then, just ignore my post.

---

