---
title: "Fuse and NTFS-3G"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by conradcliff on 2007-01-24
Ok, while trying to install fuse I get this:

thecliff@The-Conix-Box:~$ /home/thecliff/fuse-2.6.1/configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

I looked to the config log but I didn't find it. Any help would be super...

---

### Post by givré on 2007-01-24
If you want ntfs-3g without the pain of compiling everything, have a look here :
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by conradcliff on 2007-01-24
Thanks for the reply, but I'm using a 64 bit architechture and when I tried to install the easyubuntu it had some problem with the "universe" deal. So I'm trying to do it manually. Any help would be great.

---

### Post by givré on 2007-01-24
> **conradcliff said:**
> Thanks for the reply, but I'm using a 64 bit architechture and when I tried to install the easyubuntu it had some problem with the "universe" deal. So I'm trying to do it manually. Any help would be great.
```
sudo apt-get build-essential
```
should do the trick.

---

### Post by conradcliff on 2007-01-24
This is the error I get from the easyubuntu thing:

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-amd64_Packages)

---

### Post by conradcliff on 2007-01-25
Thanks for all your help, I found [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows") tutorial which did the trick for me.

---

