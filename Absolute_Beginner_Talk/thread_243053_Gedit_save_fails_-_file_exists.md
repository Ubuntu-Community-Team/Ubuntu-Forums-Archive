---
title: "Gedit save fails - file exists"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by heavyweek on 2006-08-24
Excuse me for what's probably a daft question. I am trying to edit an html file (which is on an ntfs drive) with gedit. On saving I get a message telling me that the file already exists and cant be saved, please chose another file name etc. I can edit the file with open office text editor and save without problem which seems to suggest that the issue lies within gedit or my use of it rather than with the file, file system or permissions. Any ideas as to why this might be the case or suggestions as to what Im doing wrong ?  
Thanks.

---

### Post by TFX360 on 2006-08-24
NTFS is not write supported my friend. I'll try and find some more info for you.

---

### Post by TFX360 on 2006-08-24
Try [this]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+3g") thread, be weary tough! 


NTFS writing is not supported because it isn't open source...


Kind regards,


TFX

---

### Post by benfindlay on 2006-08-24
Just copy the file off the NTFS drive into a FAT/FAT32/ext3 partition (or other compatible file system), edit it, put it on a pendrive/floppy/cd, boot into your NTFS OS and put it back again. Should work a treat then!

---

### Post by heavyweek on 2006-08-24
Thanks all for your responses. The fact that ntfs is not writeable may well be the issue. I have however, previously installed the ntfs-3g driver and have had no other write failures other than with gedit. I am now editing and saving the same file with Cream editor quite happily. All of which seems to suggest that Gedit and NTFS-3g don't play nicely together. 
Thanks again all.

---

### Post by TFX360 on 2006-08-24
Sounds like a bug to me. You should report it!

---

