---
title: "Do I need to download all these item?"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by gargoyle on 2006-07-18
I am trying to download and install a program called xfce4-appfinder. [Appfinder]("http://packages.ubuntulinux.org/hoary/x11/xfce4-appfinder")
On the page I was directed to for download are a bunch of other package. 

> #

libatk1.0-0 (>= 1.9.0)
    The ATK accessibility toolkit

#

[dep] libc6 (>= 2.3.2.ds1-4)
    GNU C Library: Shared libraries and Timezone data

#

[dep] libglib2.0-0 (>= 2.6.0)
    The GLib library of C routines

#

[dep] libgtk2.0-0 (>= 2.6.0)
    The GTK+ graphical user interface library

#

[dep] libice6
    Inter-Client Exchange library
or xlibs (>> 4.1.0)
    X Window System client libraries metapackage and XKB data

#

[dep] libpango1.0-0 (>= 1.8.1)
    Layout and rendering of internationalized text

#

[dep] libsm6
    X Window System Session Management library
or xlibs (>> 4.1.0)
    X Window System client libraries metapackage and XKB data

#

[dep] libx11-6
    X Window System protocol client library
or xlibs (>> 4.1.0)
    X Window System client libraries metapackage and XKB data

#

[dep] libxfce4util-1 (>= 4.2.1-1)
    Utility functions library for Xfce4

#

[dep] libxfcegui4-3 (>= 4.2.1-1)
    Basic GUI C functions for Xfce 

I have already downloaded 
> Download xfce4-appfinder
Download for all available architectures Architecture	Files	Package Size	Installed Size

i386 	[list of files] 	111.5 	580


I would have though the above would have taken care of everything I need but I guess I was wrong.

So do I need to download all these other programs?

---

### Post by T700 on 2006-07-18
Please see the link, How to Install Anything, in my sig.  It will explain the process and save you quite a bit of pain.

Paul

---

### Post by Jagot on 2006-07-18
If you download using Synaptic or apt-get/aptitude it will download all dependencies for you.

---

### Post by gargoyle on 2006-07-18
Jagot said:
> If you download using Synaptic or apt-get/aptitude it will download all dependencies for you.

I am unable to use Synaptic because I have not yet been able to set up my dial up modem.  I have a separate post on this already.

Can I use apt-get/aptitude command in WinXP? I have a feeling I can not but I will ask anyway.

---

### Post by T700 on 2006-07-18
> **gargoyle said:**
> Jagot said:


I am unable to use Synaptic because I have not yet been able to set up my dial up modem.  I have a separate post on this already.

Can I use apt-get/aptitude command in WinXP? I have a feeling I can not but I will ask anyway.

No, you can not.

Paul

---

### Post by aysiu on 2006-07-18
What desktop environment are you currently working out of--KDE? Gnome?

I know it can't be Xubuntu, since Xubuntu already includes *xfce4-appfinder*.

---

### Post by gargoyle on 2006-07-18
I am using the Gnome desktop. 
I do not know how to get to a KDE desktop I see there is not option for it in the log in window.

Back to my orginal question?
Do I really need all of this items?

---

### Post by aysiu on 2006-07-18
Okay.

I popped my Ubuntu live CD in and did ```
sudo aptitude update && sudo aptitude install xfce4-appfinder
``` The only additional packages it wanted to install were *libxfce4util4*, *libxfcegui4-4*, and *xfce4-appfinder*.

So that's all you need--those three packages.

So, assuming you're using x86 (not PowerPC or AMD64), you would download these three links in Windows:
[http://archive.ubuntu.com/ubuntu/pool/main/libx/libxfce4util/libxfce4util4_4.3.90.2svn+r21550-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxfce4util/libxfce4util4_4.3.90.2svn+r21550-0ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/libx/libxfcegui4/libxfcegui4-4_4.3.90.2svn+r21598-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxfcegui4/libxfcegui4-4_4.3.90.2svn+r21598-0ubuntu2_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/x/xfce4-appfinder/xfce4-appfinder_4.3.90.1svn+r21281-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xfce4-appfinder/xfce4-appfinder_4.3.90.1svn+r21281-0ubuntu3_i386.deb)

Then you'd copy them to the desktop on your Ubuntu computer and ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

