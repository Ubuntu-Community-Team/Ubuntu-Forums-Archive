---
title: "Kernel source problem"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by mariusdrg on 2008-02-28
I am a new linux user, I have just installed kubuntu version 3.5.2(I think this is right because that is what adept tells me) and when I try to install my Nvidia Geforce Fx it tells me there in no precompiled kernel so I must compile one, I follow the steps and try to compile it by myself but when I get to a make it gives me this:

If you are using a Linux 2.4 kernel, please make sure
you either have configured kernel sources matching your
kernel or the correct set of kernel headers installed
on your system.

If you are using a Linux 2.6 kernel, please make sure
you have configured kernel sources matching your kernel
installed on your system. If you specified a separate
output directory using either the "KBUILD_OUTPUT" or
the "O" KBUILD parameter, make sure to specify this
directory with the SYSOUT environment variable or with
the equivalent nvidia-installer command line option.

Depending on where and how the kernel sources (or the
kernel headers) were installed, you may need to specify
their location with the SYSSRC environment variable or
the equivalent nvidia-installer command line option.

*** Unable to determine the target kernel version. ***

How am I supose to check kernel version, or what am I supose to do? What are the header files?

---

### Post by TheDilettante on 2008-02-28
your header files are /usr/src - in konsole enter:

sudo find /usr/src -name '*header*'

and the headers file, along with the version number of the kernel you're using, will show up.

addressing the greater problem, you shouldn't be able to run kubuntu w/o a compiled kernel - as i understand it, that's like having a pile of parts that if assembled would make a car.  maybe you can try to reinstall kubuntu (if necessary, can you back up important files?) with your card in the computer, and from the livecd's konsole try to install the driver?  use google to find instructions for installing programs/files while running a live cd.

hope this works.

---

### Post by mariusdrg on 2008-02-28
sudo find /usr/src -name '*header' returns nothing.... This is probably because the folder /usr/src is empty.. I've checked it manualy and it realy is empty, it's size as a folder is 0.., I think you are right I probably should reinstall linux, maybe a better version, this version of kubuntu has many bugs...... Can you please recommend some version of Ubuntu? 

p.s. Thank you very much for your help

---

### Post by TheDilettante on 2008-02-28
There's nothing wrong with Kubuntu - I use Ubuntu myself because I like the gnome desktop, but there's nothing intrinsically wrong with Kubuntu.  If you like the way it looks or some function you can get in it but not others, you should reinstall... 

Perhaps you should start by downloading the livecd again, as the data may have been screwed up during your download.  I don't know what Kubuntu 3.5.2 is, but I'd say you should be installing Kubuntu Gutsy Gibbon, which would mean going to the Gutsy download site and selecting Kubuntu.

Try again with a fresh download, using whichever Ubuntu whose look you like the most, and install it.  If after that your card still won't install, post back here.  It just really sounds like you have a botched cd.

EDIT: if you cant find screenshots, [http://www.thecodingstudio.com/opensource/linux/screenshots/index.php](http://www.thecodingstudio.com/opensource/linux/screenshots/index.php), and look for all the 'buntu's labeled 7.10 Gutsy, NOT Hardy.

---

