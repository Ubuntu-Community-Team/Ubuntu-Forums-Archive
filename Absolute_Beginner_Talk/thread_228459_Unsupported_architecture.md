---
title: "Unsupported architecture"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by Skyrail on 2006-08-03
I have only recently found out how to install programs. Are most of the programs actually included with Ubuntu? I went to the Add & Remove programs panel and it had loads of differnt programs with unticked boxes, some of which I was interested in using. Do I have to download the actual files or should I just beable to tick the boxes? 

If it is the latter I can't doit as it says that I've got an unsupported architecture, does this mean that my hardware won't beable to run it? If so I don't mind, I'll just have to but an ethanet crossover cable, transfer files off my faster comptuer and install Ubuntu on there (thats if I really do want to, just got to think about it and make sure I get all the fiels I want transfered) So wants teh verdict?

---

### Post by tripleee on 2006-08-03
You should basically be able to click on the applications you want and click OK, and it should start downloading and installing them. This depends on having a network connection. You could install from a CD or DVD, too. How did you install Ubuntu, and which version?

I haven't seen the "unsupported architecture", can you write the names of some applications that you have tried to install which had this problem? Your architecture should be one of i386 (most likely, general PC, like one you can run Windows on), amd64, or powerpc (PowerMac) but generally, most applications are available for all three. (If you are on a SPARC or something even more esoteric, that would explain it, but then it would probably be obvious to you too.)

---

### Post by tripleee on 2006-08-03
(Sorry, double posted by mistake because I got an error message the first time.)

---

### Post by Skyrail on 2006-08-03
I've tried Blender 3D, Inkscape and a few of the games. I have isntalled off a disc from a friend, but its an official one with 6.06 LTS on it, I can tell itss the official one as its the same casing that you get from the official website. I have got Inkscape on a USB pen drive which I would like to use to instal it on the system...it still not working :( I just can't think of what it is, were they supposed to be installed in the first place? I'm just a web developer and I need some of thse programs to produce me web graphics :) (considering I can't afford PS) so...any ideas?

---

### Post by tripleee on 2006-08-03
Do you have a network connection?

What you have on the USB stick, is this a .deb file containing inkscape-0.43-4ubuntu3_i386.deb or something else? What else then?

Inkscape depends on a lot of other packages which you will need to install first. Synaptic (the Add/Remove thingy) will attempt to install these automatically, but if you are depending on a USB stick, you will need to have these on the stick, too (and figure out how to get Synaptic to read your stick).

```
Depends: libatk1.0-0 (>= 1.9.0), libbonobo2-0 (>= 2.13.0),
 libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.2-2), libfontconfig1 (>= 2.3.0),
 libfreetype6 (>= 2.1.5-1), libgc1c2, libgcc1 (>= 1:4.0.2),
 libgconf2-4 (>= 2.11.1), libglib2.0-0 (>= 2.9.3),
 libglibmm-2.4-1c2a, libgnomevfs2-0 (>= 2.13.92-0ubuntu4),
 libgtk2.0-0 (>= 2.8.0), libgtkmm-2.4-1c2a,
 liborbit2 (>= 1:2.10.0), libpango1.0-0 (>= 1.11.99),
 libperl5.8 (>= 5.8.7), libpng12-0 (>= 1.2.8rel),
 libpopt0 (>= 1.7), libsigc++-2.0-0c2a (>= 2.0.2),
 libstdc++6 (>= 4.0.2-4), libx11-6, libxcursor1 (>> 1.1.2),
 libxext6, libxfixes3, libxft2 (>> 2.1.1), libxi6, libxinerama1,
 libxml2 (>= 2.6.23), libxrandr2, libxrender1, libxslt1.1 (>= 1.1.15),
 zlib1g (>= 1:1.2.1)
```

The package manager is basically able to install anything it has in its list of available packages, but something suggests to me that your package manager is somehow hosed ... Do you have a spare machine or a vmware where you could install from scratch just to see how it's supposed to work?

---

### Post by Skyrail on 2006-08-03
At the moment I have no form of conection between any of my PCs, but soon I'm hoping to get an Ethaernet cable to connect two of them together to transfer files over from my old PC to this one I've thrown together (the one I've got problems on) so I can then install Ubuntu on to it. 

But I have got spare machines, but two of them run windows and one of them is very slow but runs slax just as a test machine (haven't a clue how to work it at the moment only got it yesterday) 

At the moment I'm completely lost, I would try and get screen shots etc, but I have yet to get the internet working on it :( so I can't really take the shots and send them over (without some hassle). Also with the code...whats that for? lol another thing I can't do is put in large blcoks of code in anywhere as I send I'm not connected to the itnernet on the ubuntu PC :( I'm hopefully getting this sorted out today hopefully or maybe tomorrw :). Its complicated with all the problems and what I would like to do and what I have done...so I'm really sorry if I have confused you. I just would like to run a few more programs and get the internet working on it :(.

---

### Post by mcduck on 2006-08-03
well, the 'add/remove' thing as well as Synaptic package manager and apt-get all only install things from internet. So they are no use for you until you get internet connection working on that machine..

Until then, you can install .deb packages manually from a terminal with a command 'sudo dpkg -i <name-of-the-package>. But this won't handele package dependencies, and you'll have hard times doing that yourself and getting every package you need. So this isn't very usefull for anything but simple apps that have very few dependencies.

---

### Post by Skyrail on 2006-08-03
> **mcduck said:**
> well, the 'add/remove' thing as well as Synaptic package manager and apt-get all only install things from internet. So they are no use for you until you get internet connection working on that machine..

Until then, you can install .deb packages manually from a terminal with a command 'sudo dpkg -i <name-of-the-package>. But this won't handele package dependencies, and you'll have hard times doing that yourself and getting every package you need. So this isn't very usefull for anything but simple apps that have very few dependencies.

Thanks for the tip :) however I tried the Live CD on my other PC I was talking about and all the programs are recognised and would be able to install (that is if I installed Ubuntu) but at the moment I'm trialling multiple distros and I'm waiting to transfer fiels off the PC I'm going to install the final one on as I've got so much junk on there. This means I'm getting what I want and then installing Linux (annoye dwith windows) to get a fresh new PC (kind of).

---

### Post by tripleee on 2006-08-04
It's not actually code, it's a listing of the packages which the inkscape package depends on. So if you transfer the inkscape .deb on a USB stick you will also need to transfer any of those packages which are not already installed (and/or available on your installation CD).

So again, what is it that you have on the USB stick?

Also have a look at [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by Skyrail on 2006-08-04
I just downloaded the Linux version of Inkscape onto my USB stick off the Insckae website...at the moment I'm trialing SuSe on that computer...but as soon as I get the files off my PC I'll beable to install Ubuntu argh, stupid music files :(

---

