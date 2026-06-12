---
title: "Firmware installation"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by jordanae on 2008-04-11
I need to install firmware for my Broadcom B43 Wireless Driver and to do that I need to install a package by typing in 
[PHP]sudo apt-get install build-essential[/PHP]
The problem is that I can't connect to the internet. Can I install that on my PC somehow and put it on a blank disk and download it that way?

---

### Post by Cypher on 2008-04-11
[Build-essential]("http://packages.ubuntu.com/gutsy/build-essential") is just a Meta package that calls out various other packages necessary to build packages.

So you COULD go the link and then follow through each of the sub packages listed there and download the DEB files. Put that onto a CD and then install it in Ubuntu..

---

### Post by jordanae on 2008-04-11
> **Cypher said:**
> [Build-essential]("http://packages.ubuntu.com/gutsy/build-essential") is just a Meta package that calls out various other packages necessary to build packages.

So you COULD go the link and then follow through each of the sub packages listed there and download the DEB files. Put that onto a CD and then install it in Ubuntu..

Thanks. I also need to run these to install packages:
[HTML]  wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..[/HTML]
And
[HTML]  export FIRMWARE_INSTALL_DIR=”/lib/firmware”
wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
tar xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
../../b43-fwcutter-011/b43-fwcutter -w “$FIRMWARE_INSTALL_DIR” wl_apst[/HTML]

---

### Post by Cypher on 2008-04-11
The two WGET commands should be considerably easier to use and get the files. Remove the "wget" portion and take the remaining "http://" text and put it into a browser through which you are currently access the Internet and it should prompt you to download/save those 2 files..

---

### Post by jordanae on 2008-04-11
> **Cypher said:**
> The two WGET commands should be considerably easier to use and get the files. Remove the "wget" portion and take the remaining "http://" text and put it into a browser through which you are currently access the Internet and it should prompt you to download/save those 2 files..
Ok. Last problem (I think). The URL you sent me wont load anymore. For some reason it keeps on timing out.

---

### Post by Cypher on 2008-04-11
Hmm..strange, the site was working when I pulled the link..and you really need that because build-essentiall essentially points to packages like "libc6-dev", "gcc", "g++", "make" and "dpkg-dev"..but as you can imagine each of these packages have dependencies of their own..so you're going to need to follow this trail to get all the packages..

---

### Post by jordanae on 2008-04-11
So is there another way? Or will I have to wait until that page comes back up?

---

