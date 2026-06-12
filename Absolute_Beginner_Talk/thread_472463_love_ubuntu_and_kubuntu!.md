---
title: "love ubuntu and kubuntu!"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by badguyanil on 2007-06-13
Well i have downloaded and used both flavors of UBUNTU. and to be frank i love both :p. but is there any way i can actually have both of then at the same time installed on my system...not seperate installations ofcourse!
What i mean is if i have an ubuntu box..is is possible for me to add the KDE GUI to it and switch between genome and kde as i wish....other distros do provide this variety! LIke SUSE10.2 has both KDE and GEnome installed................

---

### Post by forestpixie on 2007-06-13
yes you can I usedf this guide

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

:)

---

### Post by Circus-Killer on 2007-06-13
> **badguyanil said:**
> Well i have downloaded and used both flavors of UBUNTU. and to be frank i love both :p. but is there any way i can actually have both of then at the same time installed on my system...not seperate installations ofcourse!
What i mean is if i have an ubuntu box..is is possible for me to add the KDE GUI to it and switch between genome and kde as i wish....other distros do provide this variety! LIke SUSE10.2 has both KDE and GEnome installed................

first option: 
install ubuntu
once ubuntu is installed, goto commandline and run "apt-get install kubuntu-desktop"

second option:
install kubuntu
once kubuntu is installed, goto commandline and run "apt-get install ubuntu-desktop"

i think thats all that needs to be done (but do excuse me if i am wrong)

---

### Post by forestpixie on 2007-06-13
I think if you change your mind afterwards it's a bit easier to get back to where you were if you use

aptitude instead of apt-get.

Could be wrong though!

---

### Post by badguyanil on 2007-06-13
Thanks for the help....will try this one out for sure

---

### Post by earther on 2007-06-16
I have Ubuntu installed and Kubuntu on CD.  How would I install Kubuntu desktop or KDE core from the disk rather than apt-get or aptitude online. I'm still on dialup so would be faster to use the disks.

---

### Post by kevdog on 2007-06-16
Not sure if this will work, but assuming your on the Ubuntu desktop and have the Kubuntu disk in the CD player

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install kubuntu-desktop

This will modify your /etc/apt/sources.list and add your CD to the list of known repositories in addition to all known internet repositories

---

