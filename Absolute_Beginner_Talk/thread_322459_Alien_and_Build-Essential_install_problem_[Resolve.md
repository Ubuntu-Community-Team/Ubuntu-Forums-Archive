---
title: "Alien and Build-Essential install problem [Resolved]"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by VidK on 2006-12-20
Hi.. I'm trying to install the Linux driver for my Dell Wireless adapter and the driver is in RPM format. Someone suggested I use Alien to convert and install it. But, because I have no wired internet access on the Linux install (I'm using Window atm with my wireless card) - I couldn't just let Linux search and install the components. I had to download all the componenets and their dependencies. I got alot of errors, tho. I'm pretty sure I got all the dependencies. Here are there error:

rpm_4.4.1-5ubuntu2.1_i386- not satisfiable: libbeecrypt6

alien_8.64_all.deb- not satisfiable: rpm

build-essential_11.1_i386.deb
- Dependency not satifiable:gcc; I have gcc_4.0.3-1_i386, gcc-4.0_4.0.3-lubuntu5_i386, 

gcc-4.0-base_4.0.3-lubuntu5_i386

binutils_2.16.1cvs20060117-1ubuntu2.1_i386- conflicts with installed package 'binutils'

perl-modules_5.8.7-10ubuntu1_all.deb- conflicts with installed package 'perl-modules'

perl-base_5.8.7-10ubuntu1_i386.deb- conflict with perl-base

gcc_4.0.3-1_i386.deb- dependency not satisfiable: cpp ; I have cpp-4.0_4.0.3-lubuntu5_i386.deb

libc6-dev_2.3.6-0ubuntu20_i386.deb- conflicts with lib6-dev

g++_4.0.3-1_i386.deb
- not satisfiable: cpp ; I have cpp-4.0_4.0.3-lubuntu5_i386.deb

g++-4.0_4.0.3-1ubuntu5_i386.deb- not satisfiable: libstdc++6-4.0-dev; I have 

libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb, libstdc++6_4.0.3-1ubuntu5_i386.deb

libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb- not satisfiable: g++-4.0; I have g++_4.0.3-1_i386.deb

-- ty for your help, btw... David--
](*,)

---

### Post by deadgobby on 2006-12-20
Here is a link to add on a CD with no insternet. This may help you get you going.
[https://wiki.ubuntu.com/APTonCD?highlight=%28cd%29](https://wiki.ubuntu.com/APTonCD?highlight=%28cd%29)

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
 I think you are going a little hard route here. Read these links and you'll be sailing.
GObby

---

### Post by VidK on 2006-12-20
yeah... I've read the psychocat site. And, that APTonCD won't work because I don't have an internet connection on the Linux side. I'm using a wireless connection on my Desktop PC. At the moment, I'm using Windows to connect. It's a dual-boot system.

I have the drivers for my wireless addapter but they are in RPG format and need to be converted to DEB. When I try to d/l Alien - I get those errors.


David

---

### Post by aysiu on 2006-12-20
Are you using Edgy? If so, download these files:
[http://security.ubuntu.com/ubuntu/pool/main/r/rpm/rpm_4.4.1-9.1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/rpm/rpm_4.4.1-9.1ubuntu0.1_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/d/debhelper/debhelper_5.0.37.3ubuntu4_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/d/debhelper/debhelper_5.0.37.3ubuntu4_all.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.22ubuntu7_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.22ubuntu7_all.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/h/html2text/html2text_1.3.2a-3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/h/html2text/html2text_1.3.2a-3_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/b/beecrypt/libbeecrypt6_4.1.2-5_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/b/beecrypt/libbeecrypt6_4.1.2-5_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/main/r/rpm/librpm4_4.4.1-9.1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/rpm/librpm4_4.4.1-9.1ubuntu0.1_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/a/alien/alien_8.64_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/a/alien/alien_8.64_all.deb)

Transfer them (USB key, iPod, whatever) to your Ubuntu computer's desktop. Then type these commands into the terminal: ```
cd ~/Desktop
sudo dpkg -i *.deb
``` You should now have *alien* installed.

---

### Post by VidK on 2006-12-20
actally no.. I'm using Dapper... sorry I forgot to mention that.

David

---

### Post by aysiu on 2006-12-20
> **VidK said:**
> actally no.. I'm using Dapper... sorry I forgot to mention that.

David
In that case, download these .deb files instead. Same instructions apply.
[http://mirrors.kernel.org/ubuntu/pool/main/a/alien/alien_8.64_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/a/alien/alien_8.64_all.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/d/debhelper/debhelper_5.0.7ubuntu13_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/d/debhelper/debhelper_5.0.7ubuntu13_all.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.11ubuntu6_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.11ubuntu6_all.deb)
[http://security.ubuntu.com/ubuntu/pool/main/r/rpm/rpm_4.4.1-5ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/rpm/rpm_4.4.1-5ubuntu2.1_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/h/html2text/html2text_1.3.2a-3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/h/html2text/html2text_1.3.2a-3_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.11ubuntu6_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.11ubuntu6_all.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/b/beecrypt/libbeecrypt6_4.1.2-4_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/b/beecrypt/libbeecrypt6_4.1.2-4_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/main/r/rpm/librpm4_4.4.1-5ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/rpm/librpm4_4.4.1-5ubuntu2.1_i386.deb)

---

### Post by deadgobby on 2006-12-21
The AptonCD is a ISO that can burned with windows.
Gobby

---

### Post by VidK on 2006-12-21
Ok.. I did as instructed... got tons of errors... here's a copy of what I got (I transferred a text doc from Linux to WinXP so it was a big runon doc.. I tried to separate the lines the best I could):

david@david-desktop:~$ cd ~/Desktop
david@david-desktop:~/Desktop$ sudo dpkg -i *.deb
Password:


Selecting previously deselected package alien.
(Reading database ... 69971 files and directories currently installed.)

Unpacking alien (from alien_8.64_all.deb) ...
Selecting previously deselected package debhelper.


Unpacking debhelper (from debhelper_5.0.7ubuntu13_all.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from dpkg-dev_1.13.11ubuntu6_all.deb) ...


Selecting previously deselected package html2text.
Unpacking html2text (from html2text_1.3.2a-3_i386.deb) ...


Selecting previously deselected package libbeecrypt6.
Unpacking libbeecrypt6 (from libbeecrypt6_4.1.2-4_i386.deb) ...


Selecting previously deselected package librpm4.
Unpacking librpm4 (from librpm4_4.4.1-5ubuntu2.1_i386.deb) ...


Selecting previously deselected package rpm.
Unpacking rpm (from rpm_4.4.1-5ubuntu2.1_i386.deb) ...
dpkg: dependency problems prevent configuration of alien:
 alien depends on make; however:
  Package make is not installed.


dpkg: error processing alien (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of debhelper:
 debhelper depends on debconf-utils (>= 1.1.1); however:
  Package debconf-utils is not installed.


 debhelper depends on binutils; however:
  Package binutils is not installed.


dpkg: error processing debhelper (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dpkg-dev:
 dpkg-dev depends on make; however:
  Package make is not installed.


 dpkg-dev depends on binutils; however:
  Package binutils is not installed.
dpkg: error processing dpkg-dev (--install):
 dependency problems - leaving unconfigured
Setting up html2text (1.3.2a-3) ...



Setting up libbeecrypt6 (4.1.2-4) ...



Setting up librpm4 (4.4.1-5ubuntu2.1) ...

Setting up rpm (4.4.1-5ubuntu2.1) ...

Errors were encountered while processing:
 alien
 debhelper
 dpkg-dev
david@david-desktop:~/Desktop$

---

### Post by aysiu on 2006-12-21
That's weird. I guess we still need more packages, for some reason. This is what is called *dependency hell*, and it's what the package manager is supposed to take care of, but you can't use the package manager if you're not connected to the internet.

Okay, three more packages for you to download:
[http://mirrors.kernel.org/ubuntu/pool/main/d/debconf/debconf-utils_1.4.72ubuntu9_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/d/debconf/debconf-utils_1.4.72ubuntu9_all.deb)
[http://security.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.16.1cvs20060117-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.16.1cvs20060117-1ubuntu2.1_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/m/make/make_3.80+3.81.b4-1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/m/make/make_3.80+3.81.b4-1_i386.deb)

Then do ```
sudo dpkg -i *.deb
``` again.

---

### Post by lamego on 2006-12-21
Use gdebi instead of dpkg it will check for the depedencies before installing the package.

---

### Post by VidK on 2006-12-21
SUCCESS! (sort of). Everything seems to have installed without error (although there were duplicate errors from previous try... I assume that's ok, right??)

I went ahead and did an Alien conversion on the Dell's RPM-packaged Linux driver. It's a driver for my Dell 1450 -external USB wi-fi adapter. I right clicked on the package and clicked install and it seemed to install properly... but I still don't have connectivity. I checked the lights on the adapter and they aren't blinking like they should.

And ideas or suggestions?

Thanks.. David

---

### Post by aysiu on 2006-12-21
> **lamego said:**
> Use gdebi instead of dpkg it will check for the depedencies before installing the package.
But what good does that do without an internet connection?

---

### Post by aysiu on 2006-12-21
> **VidK said:**
> SUCCESS! (sort of). Everything seems to have installed without error (although there were duplicate errors from previous try... I assume that's ok, right??)

I went ahead and did an Alien conversion on the Dell's RPM-packaged Linux driver. It's a driver for my Dell 1450 -external USB wi-fi adapter. I right clicked on the package and clicked install and it seemed to install properly... but I still don't have connectivity. I checked the lights on the adapter and they aren't blinking like they should.

And ideas or suggestions?

Thanks.. David
Start a new thread on setting up a Dell 1450 -external USB wi-fi adapter.

Congratulations on getting past the first hurdle.

---

