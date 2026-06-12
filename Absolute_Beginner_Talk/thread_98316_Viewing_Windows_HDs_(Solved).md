---
title: "Viewing Windows HDs (Solved)"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by meestayenkins on 2005-12-02
I just installed Ubuntu on a clean HD, but I have 3 other HDs (ntfs) packed with all kinds of stuff like backed up cds. Is there anyway to be able to view the contents? Maybe transfer them over to the Ubuntu drive? I'd be happy just to be able to access/browse the drives though.

Thanks.

---

### Post by MetalMusicAddict on 2005-12-02
[HERE]("http://ubuntuguide.org/#windows"). There are 4 questions with answers there. 1 should apply to you. Actually since your drives are NTFS just 2. ;) Browse the rest of the guide. It will help.

---

### Post by meestayenkins on 2005-12-02
correct me if i'm wrong but arent those only applicable if youre windows partions are on teh same HD as your ubuntu?

---

### Post by aysiu on 2005-12-02
No.
For example, if Windows is on the first hard drive, it's likely to be /dev/hda1. If Ubuntu's on the second hard drive, it's likely to be /dev/hdb1. To find out where your drives live, type this in the command-line ```
sudo fdisk -l
```

---

### Post by MetalMusicAddict on 2005-12-03
When you get the output of aysiu command, youll get something like:

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7234    58107073+  83  Linux
/dev/hda2            7235        7296      498015    5  Extended
/dev/hda5            7235        7296      497983+  82  Linux swap / Solaris

**[COLOR="Red"]hda1[/COLOR]** **hd**=Hard drive and **a** is the physical drive and **1** is the partition.

With multiple drives it might be /hdb1, /hdb2 or something of the like.

---

### Post by meestayenkins on 2005-12-03
OK, issue resolved.

Thanks for giving me some direction :-D

---

