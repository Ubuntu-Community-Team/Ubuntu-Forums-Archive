---
title: "Toshiba Laptop Sound"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by the-nuke on 2008-02-26
Hi

This is my first post so please be gentle. I have a P100-429 Toshiba laptop running Gutsy. Bios version 4.2. I have no sound. Been reading posts now for several days but nothing seems to help. Anyway to cut a long story short
downloaded kernel  2.6.25-rc3 tried it and sound was there. I got rid because it caused more problems than i gained, ie WIFI problems. Anyway back on kernel 2.6.22-14-generic and back to no sound.
Can anybody give any assistance. I like gutsy and can live with no sound, but there are times that it is useful,  ie CD's

Help would be appreciated, Be aware I am a relative newcomer to the world of linux

Regards The nuke

---

### Post by Nepherte on 2008-02-26
Try installing the latest version of ALSA: [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)
Since the latest version is not in the repositories, you'll have to compile them yourself.
For instructions on compiling see the "Update to the latest version of ALSA" on [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by the-nuke on 2008-02-26
sudo cp ~/downloads/alsa*

what does this meanin relation to the following

sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2
 

Did the first two lines no problem

Does the * want me to input something, and i havent seen ~ before

regards the nuke

---

### Post by Nepherte on 2008-02-26
The * is a wild card. I means that it doesn't matter what the rest of the filename looks like. So it doesn't require any other user input at all. The ~ is just a short notation for your home directory /home/username.
For example:
```
sudo cp ~/downloads/alsa* .
```
means that it will copy alsa-driver-versionnumber, alsa-lib-versionnumber and alsa-utils-versionnumber, located in the /home/username/downloads map, to the directory you are currently in (the . dot at the end of the command). This command will of course only work if you downloaded those three files in that location. If not, you will have to point to the correct directory.

---

### Post by the-nuke on 2008-02-26
thanks

---

