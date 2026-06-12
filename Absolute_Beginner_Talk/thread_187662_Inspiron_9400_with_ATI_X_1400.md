---
title: "Inspiron 9400 with ATI X 1400"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by davetheravexxxx on 2006-06-03
I recently got an Inspiron 9400 and installed Drapper Drake and I have gotten everything to work except the graphics card.  I can only get a resolution of 1024 x 768.  To try and correct the problem I have performed the following steps that I found on another ubuntu website.

Installer file:
ati-driver-installer-8.25.18-x86.run

Make the installer file executable and run installer as root:

chmod a+x ati-driver-installer-8.25.18-x86.run
sudo ./ati-driver-installer-8.25.18-x86.run

(GUI loads: answered prompts)
- Install Driver 8.25.18 on X.Org 6.8.x
- Automatic Install

The log file is stored at /usr/share/fglrx

Make backup copy of existing xorg.conf:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

**To here I had know problems but I was slightly confused about the following steps**

Create file /etc/ld.so.conf :

/lib
/lib64
/usr/lib
/usr/lib64
/lib/tls
/usr/lib/i486
/usr/lib/i586
/usr/lib/i686
/lib/tls/i686
/usr/lib/i686/cmov
/lib/tls/i686/cmov
/usr/X11R6/lib
/usr/local/lib

Create the necessary links and cache to shared libraries:

sudo ldconfig -v

Run the ATI graphics driver configuration program:

sudo aticonfig --initial --input=/etc/X11/xorg.conf

[B]At this stage  i got the following error message.
aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory[/B]

Reboot the computer / restart X.

If anyone has any ideas about what I am doing wrong can they let me know thanks

---

