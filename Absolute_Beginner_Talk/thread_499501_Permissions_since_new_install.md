---
title: "Permissions since new install"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by ian_6800 on 2007-07-12
I had moved some files and folders to my 2nd HD before i installed Ubuntu so I was able to do a complete install of Ubuntu. The problem is that, I can access some folders but not some of the others!

Why is this?


How can i fix this?

---

### Post by twiceasworn on 2007-07-12
Well for starters we need a little more information than you have provided.

What are your system specifications?  What type of Hard Drive did you move the files to?  What type of files are they?  Also are you getting an error message when you try to access these files?  If so, could you please post the error message?

Also, I would check your messages log in ```
/var/log/messages
```

If there is anything funky going on it should let you know in that log.

---

### Post by annda on 2007-07-12
and please do that to check the permissions:
```

ls -la /path_to_my_transferred files/
```

are they owned by you or root?

---

### Post by ian_6800 on 2007-07-13
I am currently at work so I am unable to supply that information, but as soon as I get home I will be able to gibe that info to you! Thanks for your help.. Im new to Ubuntu, so give me a chance to learn all of these commands.. lol

Most of the files are mp3 and photos, there are two folders that i am unable to access but the other folder on the drive i am able to. The mp3 folder was originally on the drive to start with and I am able to access other folders on that drive exept the mp3 and the photos.

Will supply more info once finished work

---

### Post by ian_6800 on 2007-07-15
When run ----> ls -la

drwx------ 1  501 dialout         7 2007-04-28 16:11 Music
drwx------ 1  501 dialout        41 2007-07-12 19:15 Pictures




When run----> cat /proc/cpuinfo

processor       : 0
cpu             : 7410, altivec supported
temperature     : 31-34 C (uncalibrated)
clock           : 533.333332MHz
revision        : 0.3 (pvr 800c 1103)
bogomips        : 66.30
timebase        : 33290001
platform        : PowerMac
machine         : PowerMac3,4
motherboard     : PowerMac3,4 MacRISC2 MacRISC Power Macintosh
detected as     : 69 (PowerMac G4 Silver)
pmac flags      : 00000010
L2 cache        : 1024K unified
pmac-generation : NewWorld

---

