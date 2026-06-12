---
title: "&quot;./configure -&gt; make -&gt; make install&quot;"
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by Akkerkop on 2005-10-25
Looking at most of the posts i can see that whenever you want to install any packages use: "apt-get", and "./configure -> make -> make install". 

I am a WinXP & Ubuntu (newbie) user. At the moment i've got a WinXP internet connetion, GPRS (through bluetooth dongle and cellphone). I'm trying to setup a internet connection in Ubuntu. So i'm not online with Ubuntu to install any packages (no "apt-get update").

I've downloaded the following files (in WinXP), to get my connection going: 
bluez-utils_2.19.orig.tar.gz
gnome-bluetooth-0.6.0.tar.gz
obexserver_1.0-3.tar.gz

Now i want to "install" them, and i aint got a clue how to. I've tried the process "./configure -> make -> make install", but get a error: "No C compiler found...". 

What am i doing wrong? Do i miss the plot??

Please can someone advise on how to install anything without a internet connection?

---

### Post by az on 2005-10-25
[http://packages.ubuntu.com/breezy/admin/bluez-utils](http://packages.ubuntu.com/breezy/admin/bluez-utils)

Bluez-utils is in main, and I do not know if it is on the cd.  Did you search synaptic for it?  If it is available from the cd, you will see it in synaptic and can install it.  Gnome-bluetooth is in universe, so if you can get on the net withtout it, youcan install it from there and you do not have to compile it. 

[http://packages.ubuntu.com/breezy/gnome/gnome-bluetooth](http://packages.ubuntu.com/breezy/gnome/gnome-bluetooth)


To compile stuff, you need to install the compiler.  It, too, is on the cd.  Install buikld-essential.  If you need to compile a kernel module, install gcc-3.4, too....

---

### Post by Emerzen on 2005-10-25
From what I understand, you don't have an internet connection in Ubuntu yet?  You can use browse the repositories in Windows and download the packages you are looking for...they should be packagename.deb.  Transfer these files to your home directory in Ubuntu.  Then from a terminal issue the following command:

**sudo dpkg -i nameofpackage.deb**

Once installed w/ this command you can manipulate via Synaptic.

Caution: you may have to manually do this for all of the packages dependencies as well!  (You should check out the CD and see if it has any programs you need).  

If you absolutely have to compile from source, follow the above steps but grab the following packages-> build-essential & checkinstall .

---

