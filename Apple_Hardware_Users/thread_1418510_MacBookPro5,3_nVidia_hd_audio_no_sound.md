---
title: "MacBookPro5,3 nVidia hd audio no sound"
date: 2010-02-28
forum: Apple Hardware Users
---

### Post by faif on 2010-02-28
Hello all,
Just bought a Macbookpro this month. No sound please help.

System:  MacBookPro5,3 with ubuntu 9.10
kernel: Linux ubuntu 2.6.31-19-generic-pae
soundchip: nVidia Corporation MCP79 High Definition Audio (rev b1), in windows it reports: Cirrus Logic CS4206A (AB 75). Cirrus Logic now is part of nvidia.

I've added ppa mactel repository. and tried the procedure described at:
[https://help.ubuntu.com/community/MacBookPro5-3/Karmic#Sound](https://help.ubuntu.com/community/MacBookPro5-3/Karmic#Sound)

It still doesn't work. By compiling from alsa from source, it seems worse, the sound preference even couldn't pick up device. Also in
current /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
I could not find the module name for this nvidia or CirrusLogic device.

Any suggestions?

---

### Post by linuxopjemac on 2010-02-28
I read some stories that some kernels work and others don't. If I am right, you have to try 2.6.31-17, but I could be wrong. Try a few different kernels.

---

### Post by viktara on 2010-03-06
The documented approach for Karmic 5,3 should work fine now - it's been working consistently for me for a few months now:

sudo apt-get install linux-backports-modules-alsa-karmic-generic

Also, install gnome alsa mixer:

sudo apt-get install gnome-alsamixer

reboot and you should be able to unmute the sound in gnome-alsamixer.

Full instructions are here:
[https://help.ubuntu.com/community/MacBookPro5-3/Karmic](https://help.ubuntu.com/community/MacBookPro5-3/Karmic)

---

### Post by faif on 2010-03-13
Thank you viktara, recently I've got time and fixed this. the Problem was my macbook pro is 4G memory version Therefore the kernel it uses it "linux-image-2.6.31-19-generic-pae" (A pae verison of linux). Therefore instead of install:

sudo apt-get install linux-backports-modules-alsa-karmic-generic

I used:
linux-backports-modules-alsa-2.6.31-19-generic-pae

I stick on the 2.6.31-19, since the latest 2.6.31-20 seems still have problem? At least everything works fine.

---

