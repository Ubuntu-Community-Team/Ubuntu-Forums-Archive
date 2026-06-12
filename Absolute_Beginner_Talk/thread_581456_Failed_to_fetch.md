---
title: "Failed to fetch?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Gdobbs on 2007-10-19
I have tried upgrading to gutsy several times since it came out, and am always faced with 

```
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz Sub-process gzip returned an error code (1)

```

Is it just that the servers are full, or is there something wrong? Also is it possible to upgrade if I download the ISO Image for gutsy? Thanks.

---

### Post by mikeyphi on 2007-10-19
Possible silly answer!
Did you follow the guide? [http://www.ubuntulinux.org/getubuntu/upgrading](http://www.ubuntulinux.org/getubuntu/upgrading)
Are the Software sources enabled?
Is your Internet connection working? 
Have you tried a different download mirror?

 -  The ISO for Gutsy will install rather than upgrade.
Many users, me included, prefer a clean install (after saving data files)

---

### Post by Gdobbs on 2007-10-19
I've really just started using linux, and don't have any files that need saving :p Do I just install gutsy overtop of feisty? or do I need to delete feisty first?

---

### Post by Caffeine_Junky on 2007-10-19
You can just install over the top, ...I just did it :)

---

### Post by Gdobbs on 2007-10-19
Will that delete feisty? I mean so it wont give you the option of feisty in the GRUB menu?

---

### Post by FredB on 2007-10-19
Servers and mirrors are awfully under pressure...

---

### Post by marko_4454 on 2007-10-19
> **FredB said:**
> Servers and mirrors are awfully under pressure...

"under pressure" may be an understatement....
I am getting less than a KB/s :(

---

### Post by diizy on 2007-10-19
> **marko_4454 said:**
> "under pressure" may be an understatement....
I am getting less than a KB/s :(

Well, it happens, I mean the rediculous number of downloads going would bring even the strongest servers down.

Just leave it on overnight, thats what I did.

---

### Post by marko_4454 on 2007-10-19
> **diizy said:**
> Well, it happens, I mean the rediculous number of downloads going would bring even the strongest servers down.

Just leave it on overnight, thats what I did.

Yea, I know, I left it overnight as well, its 10AM for me right now and still working on it.
I am not complaining about it, I am just too excited to test it out and cant wait... :)

---

### Post by rawr215 on 2007-10-19
i am getting the fails too, and it says im up to date after installing.... im assuming because i failed to connect, thus no updates have been detected

---

### Post by louieb on 2007-10-19
Do a forum search for **_colorado_** Guy put it on the CSU server. Downloaded it this am at full speed. md5sum checked out. Burned to CD and install just fine.

---

### Post by Frak on 2007-10-19
Goto System->Administration->Software Sources->Mirror: Other->Select Best Server

It will retrieve the fastest server available, then try again to upgrade.

---

### Post by Gdobbs on 2007-10-19
Well, I just did a clean install and it seemed to work just fine. The only trouble I'm having now is with the volume control : [http://ubuntuforums.org/showthread.php?t=581935](http://ubuntuforums.org/showthread.php?t=581935)

---

### Post by Sef on 2007-10-19
> Will that delete feisty? I mean so it wont give you the option of feisty in the GRUB menu?

Yes, it will overwrite Feisty.  You will not have the option of booting into it.

---

### Post by Frak on 2007-10-19
> **Gdobbs said:**
> Well, I just did a clean install and it seemed to work just fine. The only trouble I'm having now is with the volume control : [http://ubuntuforums.org/showthread.php?t=581935](http://ubuntuforums.org/showthread.php?t=581935)
Goto System->Preferences->Main Menu->Sound->Check "Volume Control"

Then, goto Applications->Sound->Volume Control

Or to save alot of time, enter into the terminal
```
alsamixer
```

---

