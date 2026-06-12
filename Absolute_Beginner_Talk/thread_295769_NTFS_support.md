---
title: "NTFS support"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2006-11-08
Hello, I am looking to experiment with Linux on the computer I built over the summer (I call her Phoenix, but enough unnecessary info about me :D ). After some debate I have settled on starting out with Ubuntu, and as such I noticed that I should be creating a separate boot partition.  While looking further into this I also noticed that there seems to be some debate about NTFS read/write support. When I create the Linux partition/s, should I be reformatting them to FAT32?

Thanks :)

~Quintessence

---

### Post by taurus on 2006-11-08
If you want to install Ubuntu on that partition, that partition has to be ext3, NOT NTFS or FAT32.  Installing Ubuntu on FAT32 will cause many sleepless nights and trying to install it on NTFS won't get you anywhere...

---

### Post by nonpareilpearl on 2006-11-08
Does the Ubuntu Live CD allow me to format the Linux partition?

Sorry I feel like I'm drinking from a fire hose with this stuff.

---

### Post by taurus on 2006-11-08
Yes, the LiveCD has a program called gparted where you can use it to resize your harddrive, leaving some empty space to install Ubuntu.  And of course, always backup your important data on Windows first before you attend to resize your harddrive in case something might go wrong.

---

