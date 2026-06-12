---
title: "Xine DVD playback Laggy"
date: 2005-06-29
forum: Absolute Beginner Talk
---

### Post by rnaodm on 2005-06-29
whats up guys just installed ubuntu. I've done a couple automated scripts to download a bunch of applications I may need in the future, and fully updated ubuntu. I try the dvd player and I get Xine to load my movie off the dvd, but the movie is laggy. Anything i can do to smooth out the playback? Also when i load Xine, The title bar up top says Xine: There is no mrl. could this be the problem?

---

### Post by manicka on 2005-06-29
[QUOTE=rnaodm]whats up guys just installed ubuntu. I've done a couple automated scripts to download a bunch of applications I may need in the future, and fully updated ubuntu. I try the dvd player and I get Xine to load my movie off the dvd, but the movie is laggy. Anything i can do to smooth out the playback? Also when i load Xine, The title bar up top says Xine: There is no mrl. could this be the problem?[/QUOTE]
 DMA needs to be turned on for your drive. A search of the forum should solve your problem

---

### Post by rnaodm on 2005-06-29
infact it did if anyone else needs the info: > You'll have to enable dma on you drive.

To check you can do "hdparm /dev/hdd" where /dev/hdd is the location of the dvd drive .
if not then do "sudo vim /etc/hdparm.conf" and append the following

/dev/hdd {
dma = on
}

where /dev/hdd is the location of the dvd drive.

this will ensure it is enabled at boot.


To enable dma now do:

hdparm -d 1 /dev/hdd

You should be able to find out you dvd location by typing "sudo mount" when a dvd is in the drive and is mounted.

---

