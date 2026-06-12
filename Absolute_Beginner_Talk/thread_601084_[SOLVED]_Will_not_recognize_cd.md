---
title: "[SOLVED] Will not recognize cd"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by semperfiguy on 2007-11-02
Before a made my fresh install to 7.10 I made a backup of my home directory files on a cd.  I tested it in the same computer right after to see if it would get recognized and it did.  So I went through with my install I fixed most of the issues with the install and now im trying get those files back over.  But it will not recognize that there is any media inserted at all.  The install cd is recognized by itself no problem but my cd just does not get recognized.  I tried manually mounting it with ```
sudo mount /dev/scd0 /cdrom
``` but it gives the error ```
mount: No medium found
``` 

Sorry to bother you guys so much, but can you help me out again?

---

### Post by Pumalite on 2007-11-02
Check in /dev and see if you have cdrom device

---

### Post by semperfiguy on 2007-11-08
There is a /dev/scd0 device which is my cd drive.  It is also listed in fstab, but when I try and mount it manually```
sudo mount /dev/scd0
``` I get the error:
```
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
missing codepage or helper program, or other error
in some cases useful info is found in syslog - try dmesg | tail or so
```

---

### Post by Pumalite on 2007-11-08
It's supposed to mount automatically every time you put a CD in. Check your BIOS for configuration.

---

### Post by semperfiguy on 2007-11-09
And in most cases it does, but in this particular cd it doesn't automaticly mount it, and that error is why. so it must be a problem with the cd then.

---

### Post by Pumalite on 2007-11-09
Tell me what the CD-DVD is set to in BIOS and what are your options (all BIOS are different)

---

### Post by philinux on 2007-11-09
Is it a cdr or cdrw you used. And how did you burn it.

---

### Post by semperfiguy on 2007-11-09
There are no options in the bios for the cd.  The "modular bay" is cdrw and there is no way to change it.  Its a dell inspiron 1100.  

I just put in a blank cd under gnome and selected burn new cd. I dragged my .tar.gz files over and clicked burn cd.  It was a cdr

Edit:  Im starting to think this is just fluky hardware..  I fiddle with it and slam it in and clean the cd and fiddle with it forever and then it finally works then for the next cd I have to repeat the process.. I'm marking this solved..

---

