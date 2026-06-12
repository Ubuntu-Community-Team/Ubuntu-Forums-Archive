---
title: "Missing dependency that is not in Synaptic"
date: 2011-04-09
forum: Any Other OS
---

### Post by cheflo on 2011-04-09
Hello,

I'm trying to install e4rat ([http://e4rat.sourceforge.net/](http://e4rat.sourceforge.net/)), but apparently I'm missing a dependency because I end up with this error:
"Error: Dependency is not satisfiable: libboost-filesystem1.42.0 (>= 1.41)"
I'm running Linux Mint 10 (ubuntu lucid) and when I'm searching in synaptic I can't find any higher version of libboost-filesystem than 1.40.0.

What is the easiest way to update this? Do I have to download the file and compile or can I add a ppa/repository somehow? Or is my version of Mint simply too old for libboost-filesystem 1.40.0?

Btw, I think my primary partition is ext3 and not ext4, does this matter?

Regards,
Joel

---

### Post by jtarin on 2011-04-09
> **cheflo said:**
> Hello,

I'm trying to install e4rat ([http://e4rat.sourceforge.net/](http://e4rat.sourceforge.net/)), but apparently I'm missing a dependency because I end up with this error:
"Error: Dependency is not satisfiable: libboost-filesystem1.42.0 (>= 1.41)"
I'm running Linux Mint 10 (ubuntu lucid) and when I'm searching in synaptic I can't find any higher version of libboost-filesystem than 1.40.0.

What is the easiest way to update this? Do I have to download the file and compile or can I add a ppa/repository somehow? Or is my version of Mint simply too old for libboost-filesystem 1.40.0?

Btw, I think my primary partition is ext3 and not ext4, does this matter?

Regards,
Joel

Not advising you to download but there is a [.deb file.]("http://packages.debian.org/squeeze/libboost-filesystem1.42.0")Maybe to look further and see if libboost-filesystem can be upgraded with a .deb pkg. Your going to run into other dependencies when you start with one.

---

### Post by sc00ter on 2011-04-09
Add the following PPA to your software sources:

```
ppa:freefilesync/ffs

```
It contains the necessary dependencies required to get E4Rat to install on Ubuntu 10.4 (Lucid).

Launchpad page here: 
[https://launchpad.net/~freefilesync/+archive/ffs?field.series_filter=lucid]("https://launchpad.net/~freefilesync/+archive/ffs?field.series_filter=lucid")

and the PPA install instructions here:
[http://www.dlecan.com/archives/56-How-to-install-FreeFileSync-on-Ubuntu-PPA.html]("http://www.dlecan.com/archives/56-How-to-install-FreeFileSync-on-Ubuntu-PPA.html")

I went ahead and installed FreeFileSync and then installed E4Rat which then asked for some additional dependencies, installed without error.

I haven't actually tried running E4Rat yet on my Lucid system, so will post results all going well :)

**NOTE:** This is for EXT4 filesystems only so don't try running it on EXT3. If you're booting from EXT3 then I don't think this is going to make any difference to your boot speed.

---

### Post by cheflo on 2011-04-09
Hmm, I thought ext3 and ext4 was pretty similar so that tools like these would work on both file systems. But, I guess not then and maybe I shouldn't try on my main computer in case something goes wrong. Thanks for the tip though, it might come in handy later on =)

---

