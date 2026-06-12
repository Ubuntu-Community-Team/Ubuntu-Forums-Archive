---
title: "A few issues..."
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by Saur0n on 2006-07-13
Ok, I finaly decided to go with ubuntu since it seems to be the only distro that will support my cable modem and network cards etc hehe :p  but I've ran in to a few small issues I need to work out.  First of all I can't find cc which I need for compiling.  I can't seem to find it on the cd or on my harddrive install.  Is there somewhere I can dl it?  Second, what is the default root password?  It didn't ask to create one during install and it's not using my user accounts pw.  this is bad cause I can't su hehe  any help would be appreciated.  Thanks

---

### Post by Engnome on 2006-07-13
> **Saur0n said:**
> Ok, I finaly decided to go with ubuntu since it seems to be the only distro that will support my cable modem and network cards etc hehe :p  but I've ran in to a few small issues I need to work out.  First of all I can't find cc which I need for compiling.  I can't seem to find it on the cd or on my harddrive install.  Is there somewhere I can dl it?  Second, what is the default root password?  It didn't ask to create one during install and it's not using my user accounts pw.  this is bad cause I can't su hehe  any help would be appreciated.  Thanks

cc? you mean gcc? Try install build-essential. The default root password is the same as the user you created at install, however root login is disabled by default. Use sudo su to get root terminal but really it's recommended to just use sudo instead.

---

### Post by Saur0n on 2006-07-13
Hmm well it's weird.  I'm trying to install gcc but it's not configuring because it needs gcc and cc LoL  like a catch 22.    here's the output:

~/gcc-4.1.1$ ./configure
creating cache ./config.cache
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
checking build system type... i686-pc-linux-gnuoldld
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH
~/gcc-4.1.1$                   


ps.  sudo works thanks ;)

---

### Post by Rackerz on 2006-07-13
Open up Synaptic Package Manager and search 'gcc'. And I also just did a search for cc and I couldn't find it. What are you trying to install?

---

### Post by Saur0n on 2006-07-13
Still no dice.  I can't find it anywhere

---

### Post by aysiu on 2006-07-13
Put your Ubuntu CD in the drive. ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by Saur0n on 2006-07-13
Yay thank you very much aysiu, that fixed it.  ;)

---

