---
title: "Ubuntu does not support my wireless card"
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by archer75 on 2005-09-11
Not sure why they don't. It's one of the most popular Wireless cards out there, a Linksys 54g card. And there is a linux driver for it. The RT2500 driver. Mandriva supports it out of the box but that distro is just too unstable to use.

Anyways, I need the kernel sources to get the driver installed. But I can't use apt-get to get the sources because my wireless card does'nt work. 

I suppose I could try to download it in windows and then log into Ubuntu and copy it over. What kernel sources would I use for 5.10 preview release?

Anyone have a guide for installing these particular drivers? I have tried it in 4 different distros and just cannot get my wireless card working no matter what I do.

---

### Post by aysiu on 2005-09-11
You say there are Linux drivers? What form do they come in? .tar.gz? .deb? .rpm?

---

### Post by archer75 on 2005-09-11
tar.gz

---

### Post by aysiu on 2005-09-11
[QUOTE=archer75]tar.gz[/QUOTE] Sounds as if you have to install it from source. Have you done that before?

---

### Post by archer75 on 2005-09-11
Yes, I have. Several times in different distros. But never got it to work. Always some error or another. 

And I need the kernel sources too in order to even attempt this in ubuntu.

---

### Post by aysiu on 2005-09-11
[QUOTE=archer75]Yes, I have. Several times in different distros. But never got it to work. Always some error or another. 

And I need the kernel sources too in order to even attempt this in ubuntu.[/QUOTE] Whoa! I don't know much about kernel sources, but maybe this'll help?

[http://ubuntuforums.org/showthread.php?t=62037](http://ubuntuforums.org/showthread.php?t=62037)

---

### Post by archer75 on 2005-09-11
Problem is that link tells me to apt-get the kernel sources. But without a working wireless card in linux it makes it impossible to use apt-get.

I wish the ubuntu guys would just build the driver into the distro. Lots of issues can be solved with apt-get but not when your wireless card does'nt work!

---

### Post by Nequeo on 2005-09-12
[QUOTE=archer75]Problem is that link tells me to apt-get the kernel sources. But without a working wireless card in linux it makes it impossible to use apt-get.

I wish the ubuntu guys would just build the driver into the distro. Lots of issues can be solved with apt-get but not when your wireless card does'nt work![/QUOTE]
 Hi there!

To find out what Kernel you're using, type 'uname -r' at the terminal. 

Then go to whatever computer/OS you use for internet accessm and go to the following website:

[http://packages.ubuntu.com](http://packages.ubuntu.com)

Do a search for 'linux' (make sure you tell it to search Breezy, if you're using the preview), and then find the Linux Headers package that matches whatever you got from 'uname -r'. Download that onto a CD, shared partition, whatever, and then install it in Ubuntu with

```

sudo dpkg -i thePackage.deb

```

In my experience, you typically only need the source code headers to build new Kernal modules. I could be wrong... but this will probably get you sorted. 

Don't forget to 'sudo apt-get install build-essential' too, if you haven't already done so. All the compiling tools you need should be on the CD, but they have to be manually installed.

Cheers,

---

