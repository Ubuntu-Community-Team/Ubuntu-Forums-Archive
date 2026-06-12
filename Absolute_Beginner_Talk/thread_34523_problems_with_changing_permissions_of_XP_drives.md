---
title: "problems with changing permissions of XP drives"
date: 2005-05-15
forum: Absolute Beginner Talk
---

### Post by animesh on 2005-05-15
I have been trying to change the permissions of windows drives but not being able to change even as a root user by chmod ...
                 I have also edited the  /etc/fstab  file to look like
     
         proc            /proc           proc    defaults        0       0
/dev/hda7       /               reiserfs defaults        0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /windows/c      ntfs   defaults,umask=0 0 0
/dev/hda5       /windows/d      ntfs   defaults,umask=0 0 0
/dev/hda6       /windows/e      ntfs   defaults,umask=0 0 0

     after doing  this owner, group and others all have the permissions to read ,execute but still none has the permission to write,and properties show root as the owner.

---

### Post by Sam on 2005-05-15
Because you cannot write to a NTFS drive !!! (in fact, yes, but it's unstable, it may destroy your data).

Have a look on the [guide](http://ubuntuguide.org/#windows)...

---

### Post by animesh on 2005-05-15
thnks very much 4 replying so quickly 
so what should or can I do about it ?? thr is nothng abt giving write permissions on the guide in ntfs

---

### Post by i-tech on 2005-05-15
you can compile a new kernel and enable wrting to ntfs but i dont recommend it. I changed all ntfs to vfat

---

### Post by TravisNewman on 2005-05-15
[QUOTE=i-tech]you can compile a new kernel and enable wrting to ntfs but i dont recommend it. I changed all ntfs to vfat[/QUOTE]
 writing to NTFS, even if enabled in the kernel, is still spotty. You can only overwrite a file if you are writing a file of the exact same size to it. So if you open a text document, add 2 letters, save it, you corrupt something.

Long story short, don't enable NTFS write support in the kernel :)

---

### Post by Quest-Master on 2005-05-15
Yeah. I converted my NTFS to FAT32 before even starting with Linux.. it's truly been one step I can't live without. :)

---

### Post by dorris on 2005-05-15
[QUOTE=Quest-Master]Yeah. I converted my NTFS to FAT32 before even starting with Linux.. it's truly been one step I can't live without. :)[/QUOTE]
 hehe, I went a different, route, I took an old win2k box that acts as our printserve, added a little 80Gb to act as Mail share/data between windoze and ubuntu

---

### Post by animesh on 2005-05-16
well then what should I do ,if now I want to change NTFS to VFAT ? 
 I will have to format widows (all drives) ???

---

### Post by dorris on 2005-05-16
A format might be a little hazardous, and more effort than its worth,
Backup your valuable data first
a nice prog like partition magic is capable of resizing your NTFS partitions, make it just as big as it needs to be for your OS + a little free space for aaplications, and convert the leftover space to Fat32, copy data back to fat partition, share it with ubuntu!

When trying to format/create the FAT32 partition, don't believe a word the win2K/XP format tool tells you, and it will tell you the maximum size of a fat partition is 32GB, use another format tool outside windows XP, FAT32 can theoretically be up to 2TB large!
win98 will allow a format as large as 127GB.
Not sure what Ubuntu will say, haven't tried, I'd format fat with windows and ext.. with linux

---

### Post by i-tech on 2005-05-16
> well then what should I do ,if now I want to change NTFS to VFAT ? 
 I will have to format widows (all drives) ??? 
Here is what i did but dont know if it ok for you.I keep windows xp installed partition as ntfs. and create a share partition which is vfat. so the files which i need in both OS  stored in vfat partition. this might work for you. And also there are ways that make windows see ext3 file format but &#305; don't know much about it. best solution is of course formating windows and never using it again :wink:

---

### Post by animesh on 2005-05-23
thnks i have converted ntfs to vfat ,and it worked

---

### Post by ruddyconsult on 2005-07-14
When a friend installed my Ubuntu alongside XP, we created a third partition for user data from both OS that was formated with VFAT instead of NTFS. However under Linux I don't have write permission and cannot change permissions. That may be done only by the owner of root. But that's me. What could be wrong?
Thomas

---

### Post by poofyhairguy on 2005-07-14
[QUOTE=ruddyconsult]When a friend installed my Ubuntu alongside XP, we created a third partition for user data from both OS that was formated with VFAT instead of NTFS. However under Linux I don't have write permission and cannot change permissions. That may be done only by the owner of root. But that's me. What could be wrong?
Thomas[/QUOTE]

you need a super nautilus to change the persmissions:

> gksudo nautilus

---

