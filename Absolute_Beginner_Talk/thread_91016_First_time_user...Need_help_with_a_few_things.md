---
title: "First time user...Need help with a few things :\"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by Komataguri on 2005-11-16
this is my first serious foray into the linux world... Which is why I nuked my XP install and put ubuntu in its place instead of dualbooting :D


However, I'm having some problems that I can't seem to figure out or find answers for... Maybe I overlookd them, if I did I'm sorry :???: 



But.... I uninstalled the default driver for my 9600pro and reinstalled them according to the guide in [thread]("http://ubuntuforums.org/showthread.php?t=85899")


however I can't get my S-video output to work. It just shows garbled static on my TV when I switch to the S-Video imput on it.  I use my PC for watching DVDs and videos, so S-Video is kind of important to me..


If anyone can help me get it to working I would be seriously appriciative :)


__________

Another problem I'm having is accessing my NTFS drive with Captive NTFS.  Says I don't have permission to accesss the drive when I try to view it in /mnt/drive name 

I saved the files it wanted from my windows install before nuking it, and It said it completed successfully when I installed it [ using captive-install-acquire ]

I just want to get access to that data so I can get it off the drive and convert it to a linux file system. 

Only reason I installed Linux first is a friend of mine who is knows just about everything about linux told me that I'll be able to access the drive just fine from Linux with Captive NTFS, and now I can't get in contact ith him [ he's busy alot ]


any help on this matter would also be seriously appriciated :) 


Thankyou.

---

### Post by aysiu on 2005-11-16
I have no experience with Captive NTFS--supposedly it lets you have write ability to NTFS. I just made a FAT32 partition to write to. NTFS is read-only for me. If you want read-only in the meantime, you can look here:

[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by bonzodog on 2005-11-16
it depends how the ntfs partition is mounted- it 's possible its mounted with root permissions only. try starting captive ntfs off the commandline and put 'sudo' in front of it, like so;

$sudo captiventfs    (or whatever the filename is)

---

