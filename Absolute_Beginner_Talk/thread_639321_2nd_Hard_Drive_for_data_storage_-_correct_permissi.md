---
title: "2nd Hard Drive for data storage - correct permissions?"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by inzania on 2007-12-13
Hey guys - I'm just making the switch to Ubuntu from Windows.  I have a 2nd hard drive in my laptop which I use for music, data, etc (but I keep both OSs installed on the primary drive). I can explore the 2ndary drive in Ubuntu, but I cannot seem to use it properly.  For example, any attempt to write to the drive says I do not have the right permissions.  I try to play music from the drive in Rhythmbox and it just skips each of the songs, unable to play them.  I'm assuming this is a permissions problem - any idea how to fix it?

---

### Post by muteXe on 2007-12-13
If the drive is NTFS i think it's treated as read-only by linux.  I think :)  

Tom

---

### Post by kpkeerthi on 2007-12-13
How is it formatted (NTFS/EXT3)? How are you mounting the drive?

---

### Post by shadow-of-sin on 2007-12-13
If it is formatted as NTFS, to write to it you will need to install ntfs-3g , just follow this guide:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by bigken on 2007-12-13
the reason rythem box is skipping the tracks is you dont have the right codecs installed


in add/remove go to other  and select restricted extras to install this should slove it for you

---

### Post by kpkeerthi on 2007-12-13
> **shadow-of-sin said:**
> If it is formatted as NTFS, to write to it you will need to install ntfs-3g , just follow this guide:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

**Be warned. That guide is for Dapper and Edgy.** Step 1 & 2 are not required as ntfs-3g is now available in gutsy repository. So you can jump to Step 3 straightaway.

---

### Post by bigken on 2007-12-13
you can also install the ntfs tool from add/remove

---

