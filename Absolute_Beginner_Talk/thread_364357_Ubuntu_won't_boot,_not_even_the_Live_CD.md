---
title: "Ubuntu won't boot, not even the Live CD"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by panti19 on 2007-02-18
I've installed ubuntu and it worked perfectly. after a couple of restarts, Ubuntu would not start after the boot loading bar.
i was just  a black screen.
i wanted to reinstall,  put the Live CD and Ubuntu didn't start in a Live session either. After the loading bar, i got a black screen.
i reformatted the hard disk using NTFS with the Windows XP install disc.
i booted the live cd agan and it didn't start. the black screen again.
i had to install windows to be able to write this message.
please help.
i want my linux baaack. :(

---

### Post by panti19 on 2007-02-18
my system specs are (keep in mind that i've installed ubuntu and it worked,i just did 3rd restart (i think ) and it stopped working
AMD Sempron 1,6 Ghz
512 RAM
Ati radeon 9200 Pro
SoundMax audio

---

### Post by panti19 on 2007-02-18
please.. i really hae windows... i want my linux back

---

### Post by OBnascar on 2007-02-18
> **panti19 said:**
> 
i reformatted the hard disk using NTFS with the Windows XP install disc.


I am trying to understand what you did here.

You actually formated your Linux partitions with NTFS ?

I would download the Gparted Live CD (see my signature) and use that to format the Linux partition to file system ext3 and go from there.

---

### Post by Bartender on 2007-02-18
The ATI 9200's are troublesome cards.  The problem is probably with xorg.  Take a look at some threads that talk about how to boot up using the 'vesa' setting.  I've never had to do this so don't know the specifics, but sure that if you only have one problem that card is it.

---

