---
title: "Installing NVU on Ubuntu 5.10"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by andym1966 on 2006-05-09
Hi,
I'm trying to install the web editor NVU.
I've downloaded    nvu-1.0-pc-linux2.6.10-gnu.tar.bz2  from [http://www.nvu.com/download.html](http://www.nvu.com/download.html)

I extracted it using  tar xvf and the following folder and contents is created in my Home folder:
andrew@ubuntu:~/nvu-1.0$ dir
bloaturls.txt      libnspr4.so         libxpcom.so             regxpcom
chrome             libnss3.so          libxpistub.so           res
components         libnssckbi.so       LICENSE                 run-mozilla.sh
defaults           libplc4.so          mangle                  shlibsign
elf-dynstr-gc      libplds4.so         mozilla-xremote-client  xpcshell
greprefs           libsmime3.so        nsinstall               xpicleanup
icons              libsoftokn3.chk     nvu                     xpidl
libgkgfx.so        libsoftokn3.so      nvu-bin                 xpt_dump
libgtkembedmoz.so  libssl3.so          nvu-config              xpt_link
libgtkxtbin.so     libxlibrgb.so       plugins
libmozjs.so        libxpcom_compat.so  regchrome

But what do I do now?  I've tried double clicking on nvu-bin and nothing happens.  Am I doing the right thing to install NVU???
I've seen elsewhere on this forum to type:
sudo apt-get install nvu 
but that doesn't work either.

Any help much appreciated. 
Andrew (a total newbie to linux)

---

### Post by K2712 on 2006-05-09
nvu is available through apt-get or synaptic, but you have to enable the universe/multiverse repositories.

In Synaptic->Settings->Repositories-> Check all universe and multiverse sources->Hit OK then hit reload in main window

or

add the following lines to your /etc/apt/sources.list:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 

Then:   

sudo apt-get update
sudo apt-get install nvu

---

### Post by TheTopPenguin on 2006-05-19
How do you install NVU without using apt-get? The machine I'm using is not connected to the internet.

---

### Post by aysiu on 2006-05-19
[QUOTE=TheTopPenguin]How do you install NVU without using apt-get? The machine I'm using is not connected to the internet.[/QUOTE] That's interesting. So you use Nvu to design websites, but you aren't connected to the internet? Would you design the websites and then copy the .html, .php, and .css pages to a computer that *does* have internet and then upload the pages from that other computer? I'm just curious.

In any case, the best way to do it is to download the .deb file for Nvu on the other computer, transfer it to your Ubuntu computer and put it on the desktop and then paste these commands into the terminal: ```
cd ~/Desktop
sudo dpkg -i nvu*.deb
``` It won't resolve dependencies for you, but that's how you'd do it.

---

### Post by sleepy1364 on 2006-05-25
i download nvu package (.deb) from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) but when i try to install this package with dpkg -i command . dpkg says that its not debian package ! (i use ubuntu 5.10 (breezy));

i download this package :
nvu_1.0-0ubuntu3_i386.deb  

there is no other package on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) .

---

### Post by aysiu on 2006-05-25
That's weird. Can you post exactly what you typed and exactly the error you got?

---

