---
title: "Yamaha Sound Card-no sound"
date: 2005-06-29
forum: Absolute Beginner Talk
---

### Post by maxpro4u on 2005-06-29
Hello-
Just installed Ubuntu today and trying to learn about it. My Yamaha DS-XG sound card is not working (works in w2k), I really don't know how to go about fixing it. In Sound and Video/Volume Control,I have selected my sound device but no go.
-max

---

### Post by poofyhairguy on 2005-06-29
Here is a howto I found:

[http://www.linux-sxs.org/multimedia/yamdsg.html](http://www.linux-sxs.org/multimedia/yamdsg.html)

Its a little advanced....but at least it exists.

---

### Post by az on 2005-06-29
[https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)

---

### Post by maxpro4u on 2005-06-29
I'm still having trouble. After closer examination I realized that the sound is onboard-not a card. I don't know if this makes a difference or not. I tried the instructions here- [http://www.linux-sxs.org/multimedia/yamdsg.html](http://www.linux-sxs.org/multimedia/yamdsg.html)  but when I got to the ./configure I got- cc not found. I used the file  alsa-driver-0.5.8a.tar.bz2 
-max

---

### Post by poofyhairguy on 2005-06-29
[QUOTE=maxpro4u]I'm still having trouble. After closer examination I realized that the sound is onboard-not a card. I don't know if this makes a difference or not. I tried the instructions here- [http://www.linux-sxs.org/multimedia/yamdsg.html](http://www.linux-sxs.org/multimedia/yamdsg.html)  but when I got to the ./configure I got- cc not found. I used the file  alsa-driver-0.5.8a.tar.bz2 
-max[/QUOTE]


I got the answer for you. You need to install this package and whatever its dependanies are:

> sudo apt-get install build-essential

---

### Post by maxpro4u on 2005-06-29
Thanks- that got me a lot closer. Now I just need to edit the config files.
-max

---

### Post by maxpro4u on 2005-07-03
Well there was no config file in ect folder-so I downloaded the latest drivers,ran through the steps again and during config got this error message-
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
Do I need to install something else? I am going to need to read more.
-max

---

### Post by poofyhairguy on 2005-07-04
[QUOTE=maxpro4u]Well there was no config file in ect folder-so I downloaded the latest drivers,ran through the steps again and during config got this error message-
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
Do I need to install something else? I am going to need to read more.
-max[/QUOTE]


install the kernel source and headers. such in synaptic for those two terms.

---

