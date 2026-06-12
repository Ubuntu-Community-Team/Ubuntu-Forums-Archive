---
title: "Where to Install Anti-virus for linux workstation?"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by webmiester on 2008-04-13
Hi guys,

Im still quite new with linux ubuntu.  Ive found very interesting Anti-virus programs for Linux...  The theory of the programs is that they will scan Windows partitions and Windows workstations connected to a linux server!  That sounds really nice :)

So I downloaded the Avira workstation for linux and the filename of the download is "antivir-workstation-pers.tar.gz"

The content of the file is a folder named "antivir-workstation-pers.2.1.11-21...
and the content of that folder are 15 objects namely folders named as:

1) bin
2) contrib
3) doc
4) etc
5) gui
6) legal
7) pgp
8) script
9) vdf

files:
10) .installrc
11) hbedv.key
12) install
13) LICENSE
14) LICENSE.DE
15) README

My question:

What am I supposed to do with these files?  Where am I supposed to expand them to?

I got a similar file for my frostwire and I ended up expending it on my desktop... Im sure there is a "cleaner" way of doing this, right?  So which directory am I supposed to expand these files into so that I keep my linux directory well organized.  Thanks so much

---

### Post by halitech on 2008-04-14
if you want to install an antivirus, check Synaptic and install one from there but unless you have a windows partition, you don't really need one (I'm sure others will chime in here with why you don't so I won't bother). 

far as installing, normally if you download a tarball (form of zip file used with *nix) then you open a terminal and cd to the folder where the files are and run ./configure and ./make to install unless there are other instructions included with the readme file.

---

### Post by original_jamingrit on 2008-04-14
the two files INSTALL and README can be opened up as text files, they should have more information.  Unpack the tar.gz file, and use gedit or nano to read them.  They will probably instruct you to run a script that places those files for you.

Cheers

---

### Post by wormser on 2008-04-14
You should take a look at the README file.  Compressed files can have different methods of install.

---

### Post by mikewhatever on 2008-04-14
It's a good idea to read the Readme, as others have mentioned. To install, you should probably run the install file with <./install>. I am not sure you get an option of choosing the location at all, but if you do, there should be the default one already chosen.

---

### Post by old_geekster on 2008-04-14
Here is a link to "HowTo Install AVG":

[http://www.ubuntugeek.com/install-avg-antivirus-in-ubuntu-desktop.html](http://www.ubuntugeek.com/install-avg-antivirus-in-ubuntu-desktop.html)

I use AVG in Windows and have for several years.

---

### Post by MrFSL on 2008-04-14
I second the use of AVG... it just saved a friends Winblows box using an Ubuntu Live disk.

Check this out:
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by webmiester on 2008-04-14
> **halitech said:**
> if you want to install an antivirus, check Synaptic and install one from there but unless you have a windows partition, you don't really need one (I'm sure others will chime in here with why you don't so I won't bother). 

far as installing, normally if you download a tarball (form of zip file used with *nix) then you open a terminal and cd to the folder where the files are and run ./configure and ./make to install unless there are other instructions included with the readme file.


yeah, I have a windows partition on this machine.  its been my dream to be able to scan the windows partition using linux, considering that when the virus has loaded into the memory when running windows, chances are, the virus will be hard to catch.

Thanks for the recommendation of AVG, but I would like to try something else.  The Avira seems to have the highest detection rates among the free antiviruses, according to a youtube and a website on antivirus detection testing I found.

---

