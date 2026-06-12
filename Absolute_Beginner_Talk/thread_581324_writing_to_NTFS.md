---
title: "writing to NTFS"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by orthiles on 2007-10-19
I heard there's a way to write to NTFS drives. I was wondering how stable is this exactly? is it worth it to reformat the drive to a different file system? (I need both xp and linux to be able to read/write to the drive) the drive is nearly full and I'd have to back up a lot of data to reformat. what should I do? just make the ntfs drive writable or reformat it (and to what filesystem)?

---

### Post by Qwerty_ on 2007-10-19
```
 sudo apt-get install ntfs-config
```

then run

```
sudo ntfs-config
```

Then click which drives you want to write to that are in NTFS

---

### Post by LowSky on 2007-10-19
well to write data you need a program called NTFS-3g and just turn on read/write support
its availible in synaptic and add/remove

if you want to format choose FAT32, Linux and Windows can read and  write to it natively, but FAT32 can only support files smaller than 4GB. Kind of a win/lose but it works.

---

### Post by ltcolfury on 2007-10-19
> **orthiles said:**
> I heard there's a way to write to NTFS drives. I was wondering how stable is this exactly? is it worth it to reformat the drive to a different file system? (I need both xp and linux to be able to read/write to the drive) the drive is nearly full and I'd have to back up a lot of data to reformat. what should I do? just make the ntfs drive writable or reformat it (and to what filesystem)?

 I am using 7.04, I'm not sure what version you are running. (On a side note, I use 2 Internal HD's, one for Windows and another  HD for Linux. I use Linux 99.9% of the time)

I was able to access my Windows Internal HD already so I was trying to get Ubuntu to see my new External HD. (It has NTFS on it)

I downloaded NTFS-3g from Automatix  then rebooted. After I rebooted my External HD was listed on my desktop and I was able to access the drive.(R/W) After I rebooted again, I wasn't able to access it again. I then went into the Package Manager and Downloaded the other NTFS package which Automatix did not install. (NTFS-Config)

Afterwards, I went into* Applications/System Tools/NTFS Configuration Tools*...I checked off External HD and it appeared. (Actually both the Interal & External NTFS appeared on the desktop even though I can access the Internal through my Home folder)

This was the only way I was able to get it to work. Sometimes after I reboot I won't be able to access it but I just do the Applications/System Tools...etc. procedure again it works.

Sorry for the long post but I wanted to make sure it was explained in detail to assist you. Again, the exact procedure I mentioned above worked for me and I did a lot of research so I can R/W to the drive. 

Let me know how you make out.

---

### Post by LowSky on 2007-10-19
Good reason not to use Automatix...lol

---

### Post by ltcolfury on 2007-10-19
> **LowSky said:**
> Good reason not to use Automatix...lol

You're right....LOL I know but...I tried everything to get it to work. Funny thing...it was the only way I could get it working.

---

