---
title: "HELP!! Complete system failure!!"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-08-10
I was trying to install Vmware and it worked. Only problem was Windows asked me to re-activate. I then went from the virtual machine to the real partition where Windows started up fine and re-activated itself. Except for now when I go back to Ubuntu it has COMPLETELY FAILED. The text comes up at the beginning saying hda3 has errors and a check will be forced. The check fails. The error that comes up is duplicate or bad block in use. It then opens up a maintenance shell where I am informed that apt-get is not installed. 

How do I get Ubuntu working again???

---

### Post by skymera on 2007-08-10
i have no idea. O.o
but i would reinstall,. if you kept a speerate home partition, you wont lose your pics, music etc

---

### Post by philinux on 2007-08-10
Dont panic. This has happened to me before.

once its gone through its reporting of bad blocks etc and give you the command prompt type in 

fsck -v  (this switch means be verbose) it will start a check again but this time after a short while it will ask you if you want to re-write each block, just answer yes. Fixed mine like this last night

---

### Post by Paulmd on 2007-08-10
> **Wake Rider said:**
> I was trying to install Vmware and it worked. Only problem was Windows asked me to re-activate. I then went from the virtual machine to the real partition where Windows started up fine and re-activated itself. Except for now when I go back to Ubuntu it has COMPLETELY FAILED. The text comes up at the beginning saying hda3 has errors and a check will be forced. The check fails. The error that comes up is duplicate or bad block in use. It then opens up a maintenance shell where I am informed that apt-get is not installed. 

How do I get Ubuntu working again???

Find out it your hard drive is good, first. Download the hard drive diagnostic program from the manufacturer of the hard drive. If it tests good, then you can do the fsck stuff. But if not, theres really no point other than to salvage data.  The hard drive would then heed to be replaced, and Ubuntu reinstalled.

---

### Post by ukripper on 2007-08-10
Run fsck from the Live CD

---

### Post by mercuccio on 2007-10-03
fsck -v worked fine to me. I did found my hard drive check program at Hitachi's web site, but didn't care to run it. Reading the read-me files I learned that all it would do is to check the disk and then replace the bad-blocks. The fsck command did the same.

Of course, the vendor's program had some other features, that might be useful on other situations. 

Thanks to all for the help

Mercuccio

---

### Post by ukripper on 2007-10-04
I am glad it worked for you. fsck is inbuilt command on linux systems to check for bad blocks and vendors do have their own utilities which i would use if fsck won't find the problem.

---

