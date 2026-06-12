---
title: "Parallels Tools Problem"
date: 2008-12-16
forum: Apple Hardware Users
---

### Post by bryan4134 on 2008-12-16
Trying to install Parallels Tools with Ubuntu 8.04 running on Parallels 3.0.   The installation starts and then halts with an error message about Xorg.  Below is the terminal dialog:

bryan4134@Ubuntu:/cdrom$ sudo sh parallels-tools.run
Verifying archive integrity... All good.
Uncompressing Parallels Tools for Linux.................................................................................................
You are about to start installing Parallels Tools. Save your data and close all
applications to prevent data loss during possible X-Server restart.
Continue ? [Yes/No]:yes
You are about to start installing Parallels Tools. Save your data and close all
applications to prevent data loss during possible X-Server restart.
Continue ? [Yes/No]:Yes
Found xorg version 1.4.0
Installation for xorg.1.4 not found.
 
Any ideas how to cure this error message.

Thanks, Bryan

---

### Post by cyberdork33 on 2008-12-16
hmm. make sure that you have the latest updates for parallels. It should work with Xorg 1.4

---

### Post by jltnol on 2009-01-22
Hey there.


Looking for your assistance again for a Ubuntu Noobie.


As it turns out, I've managed to get pretty far down the path here... I've gotten Ubuntu up in running in Parallels, and as a native boot, but just need a bit of help in Terminal.

I'm trying to install Parallel Tools, and there is a CD image on the desktop.  I've opened up Terminal, and am trying to navigate to it to run the installer.

However, can't figure out the command to change directories to do the install.

I've looked at the UNIX commands, and know that CD gets me half way there... but still.. I can't figure it out.

Also, dragging the disc icon to the terminal doesn't help either.. :(

Once I'm IN the proper directory, is the install command ./install?

Much Thanks

---

### Post by cyberdork33 on 2009-01-22
> **jltnol said:**
> Hey there.


Looking for your assistance again for a Ubuntu Noobie.


As it turns out, I've managed to get pretty far down the path here... I've gotten Ubuntu up in running in Parallels, and as a native boot, but just need a bit of help in Terminal.

I'm trying to install Parallel Tools, and there is a CD image on the desktop.  I've opened up Terminal, and am trying to navigate to it to run the installer.

However, can't figure out the command to change directories to do the install.

I've looked at the UNIX commands, and know that CD gets me half way there... but still.. I can't figure it out.

Also, dragging the disc icon to the terminal doesn't help either.. :(

Once I'm IN the proper directory, is the install command ./install?

Much Thanks

Open Terminal.
do 'cd /media/cdrom'
This is navigate to the location where the cd is mounted.
to look at the files there, run 'ls' (that is an L)
there should be several files there, including on that contains documentation for installing.

I am unsure the specific filename, but you can use ls to check it, and then type the command as you have already, but with sudo in front (this gives administrator permission for the command).

```
sudo ./install-parallels-tools.sh
```
or something like that.

---

### Post by jltnol on 2009-01-22
EXCELLENT!!!!


Was able to navigate to the CDRom... and use the sudo ./install command and all is well

Thanks so much for your help and support.

---

