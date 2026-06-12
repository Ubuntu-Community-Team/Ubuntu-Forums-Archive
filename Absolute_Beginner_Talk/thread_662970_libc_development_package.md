---
title: "libc development package"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by stevro on 2008-01-09
Hi there ... I have just installed Ubuntu 7.10 on my system (trying Ubuntu for the first time!) and am now trying to install the drivers for my Nividia 7900GS. OK ... I have got as far as getting the file (NVIDIA-Linux-x86-159.07-pkg1.run) to go but then it gives me the message that "no precompiled kernel interface was found to match your kernel" and a note asking me to install my "libc develpment package".

Here I hit a brick wall and can somebody please help me. The computer that Ubuntu is installed on does not have an internet connection so I have to do everything manually (learning the commands is half the fun!).

Can somebody please guide me. 

Thx.

---

### Post by perlluver on 2008-01-09
Check both of the guides in my signature.  They will answer your question.

---

### Post by stevro on 2008-01-10
Thank you so much for that ... I got it working just fine!

---

### Post by Huub Vlemmings on 2008-02-25
Stevro,

I've encountered exactly the same problem, searched all over the web for it. I'm curious about what you did to solve the problem. I tried to read some of perlluver's guides but that's just too much alchebra to me.

Thanks!

/edit

I installed it trough installing an internet connection; I think Ubuntu itself needs to be updated as well before everything runs smooth (libc package is a part of that)
Stevro's answer:

How to install Nvidia Drivers on Ubuntu Gutsy V7.10

*Download the Driver File NVIDIA-Linux-x86-169.07.pkg1.run from the Nvidia website.
*Put it somewhere in your system (on the Desktop will do) where you will remember.
*Download the libc development package from the Ubuntu web site (libc6-dev_2.6.1-1ubuntu9_i386.deb).
*Log in as root.
*Install the libc development package. The .deb files are self extracting so you can just double click the icon.
*Log out.
*Close the X Server (Ctrl+Alt+F1).
*Log in as root user.
*Type "sudo /etc/init.d/gdm stop" to stop the X Server. (same command with "start" at the end to restart the X Server).
*Type "sh NVIDIA-Linux-x86-169.07-pkg1.run" to install the driver.
*It should install automatically.
*Re-start the X Server (refer above).
*Once Gnome is up, open synaptic and search for the nvidia-common-kernel. Remove it. It is only needed to compile the driver.

---

### Post by Lukky on 2008-05-17
[QUOTE=Huub Vlemmings;4404253]Stevro,




*Download the libc development package from the Ubuntu web site (libc6-dev_2.6.1-1ubuntu9_i386.deb).

Can someone give me a link to this downlaod. I am find all kinds of packages real similar to that. I am running 32 bit ubu 8.04 AMD 

Thanks Dustin

---

