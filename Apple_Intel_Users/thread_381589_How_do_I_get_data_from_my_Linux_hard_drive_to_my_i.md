---
title: "How do I get data from my Linux hard drive to my iMac?"
date: 2007-03-11
forum: Apple Intel Users
---

### Post by thenetduck on 2007-03-11
Hi, 
  I just purchased an iMac for my parents and us both the Mac OSX for multimedia and the Ubuntu desktop for pretty much everything else. I need to know how I can get files from one computer  to another. I have a lot of files that are in the GB's and need to be transfered. I wasn't able to figure this out because I formated my external hard drive with the Mac OS (journaled) and Ubuntu would read it fine, but wouldn't write to it. I don't have permissons. Also, I can just "sudo mv" it to the external. Does anyone know what I can do? 

 The Net Duck

---

### Post by ouilsen on 2007-03-11
I'd suggest 2 ways. 

1) Make the external drive hfs+ without journaling. Open a terminal in OS X and type
```
sudo diskutil disableJournal /dev/sdaX
```

where "X" is your external harddrive. Maybe it's even possible to do it via the disk utility.

2) Use samba. It's maybe a bit strange, since there's no Windows machine involved. I think it's easy to set up.

---

### Post by thenetduck on 2007-03-11
Hey thanks, 
  What is journaling anyway?

---

### Post by ouilsen on 2007-03-11
If I remember correctly:

Without going into the general case of journaling, the purpose here is to keep your filesystem free of corruption. The journal describes the last state of your filesystem where it was stable. 

Imagine you are writing a file to your disk and power shortage occurs. Next time you boot, the disk is checked for errors. By using the journal, fsck is now able to determine your corrupted file, since it is NOT yet in your journal.

IMO, in theory it is always possible to shape a filesystem in a way that it won't need journaling. But it has the advantage of staying backwards compatible with older filesystems. Thats why you can just turn off the journal file and mount your "ext3" as "ext2". Same with hfs+.

Journaling is a tradeoff. You lose speed and get stability.

So in a few words: it's a log file of your filesystem.

---

### Post by cyberdork33 on 2007-03-12
Ubuntu reads the permissions of the files in your OSX partition, you should be able to mount it ignoring permissions although that might screw up something in your OSX filesystem.

---

