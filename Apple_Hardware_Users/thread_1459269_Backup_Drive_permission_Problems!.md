---
title: "Backup Drive permission Problems!"
date: 2010-04-21
forum: Apple Hardware Users
---

### Post by Ravernomina on 2010-04-21
alright im trying to move my files from my back up drive to my HDD. The Hard drive is HSF+. Now when i opened the drive i noticed i was locked out. so i log into nautilus as root and tried to change the file permissions to let me get into my backup files. But because its HFS+ i cannot get into the file system to write to the drive that i can look and use these files. Assistance please? In a NutShell can some one tell me how to write to HFS+ File systems on a Intel Macbook Pro 5,4? Thanks!

---

### Post by linuxopjemac on 2010-04-21
I would start with disabling journaling from within OSX. 

[http://mac.linux.be/content/how-access-files-osx-linux](http://mac.linux.be/content/how-access-files-osx-linux)
[http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=94](http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=94)

---

### Post by Ravernomina on 2010-04-21
None of that if working

---

### Post by linuxopjemac on 2010-04-21
Write access to an OSX HFS partition is another thing. I think that Apple made it very hard to do that. I never tried it myself, but it would probably only work if you have the same user id (UID)...

---

### Post by Ravernomina on 2010-04-22
i got it. i moved everything to the root home folder. then formated the drive, the backup drive to NTFS thus remove all of the file permissions. then logged into root and moved it all to the NTFS drive then moved it to my folder giving me my permissions.

---

### Post by linuxopjemac on 2010-04-22
Conclusion Apple's own HFS format locks you in. It is also not stable when disks are full:
> 
I have had to reinstall MacOSX 5 times in the last 5 years due to the fact that HFS is so utterly brain-dead (and MacOSX doesn't handle full disk conditions very well). I have only once have ever had to reinstall Linux/Ubuntu over the last 15 years I've been using it. Ext2/ext3/ext4 is much more reliable and Linux handles full hard drives much better.


see [this thread]("http://ubuntuforums.org/showthread.php?t=1046568&page=5#47").

So my own conclusion, made it several years ago, switch to Linux. Dare to think different ;)

---

### Post by Ravernomina on 2010-04-22
> **linuxopjemac said:**
> Conclusion Apple's own HFS format locks you in. It is also not stable when disks are full:



see [this thread]("http://ubuntuforums.org/showthread.php?t=1046568&page=5#47").

So my own conclusion, made it several years ago, switch to Linux. Dare to think different ;)

I've known that for so long :P. Now i Understand haha :lolflag:! Thanks Again for all your help :D

---

