---
title: "ubuntu 9.10 live disc help needed"
date: 2010-01-29
forum: Apple Hardware Users
---

### Post by hammmondr on 2010-01-29
i just downloaded ubuntu9.10 to run as a live disc on my ibook g4 800mhz 256ram my harddisc is broken i downloaded hedge hodge 5.1 or something last night and followd the instruction to put it on disc and that work fine just no wireless so i download the lastest ubuntu from there website and followed there disc burning instruction now when i start the ibook it just goes to that annoying apple with the loading symbol under where as when i put in hedge hog version 5 and press C it starts ubuntu what can or should i do would i be better downloading another version any help would be grateful

---

### Post by avtolle on 2010-01-29
I hope I interpreted your post correctly.

From 7.10? the live CD, due to its graphical installer, requires a minimum of 384 mb RAM to run. You indicate 256 MB RAM. If you wish to install 9.10 ppc version (see sticky above for download information), you should download and install the alternate cd iso. 

Alternatively, when you downloaded 9.10, ppc version, did you perform a md5sum check in the iso before burning to disk? 

Just reread your post, and noticed you have a bad hdd, which, to me, means you are trying to run from the cd. If so, you may want to look at Xubuntu, which does not have as stringent RAM requirements,  IIRC, to run from the live cd.

---

### Post by LtPitt on 2010-01-29
If I've understood correctly you should find what you need here:

[http://cdimage.ubuntu.com/ports/releases/9.10/release/]("http://cdimage.ubuntu.com/ports/releases/9.10/release/")

I do agree with *avtolle*: xubuntu could be a great choice for you :)

Download a basic Ubuntu [clicking here]("http://cdimage.ubuntu.com/ports/releases/9.10/release/ubuntu-9.10-server-powerpc.iso")
After you've done with the install just log in and digit:

sudo apt-get install xubuntu-desktop

When it's over just digit:

startx

Have fun! :)

ps
Please read the f.a.q. and search the forum before asking :)

---

