---
title: "creating a partition on existing install"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by gredawarha on 2007-12-22
Hi good people.

I have researched the web and this site but cant seem to find an answer to my question.  Apologies if I have missed it somewhere.

Any help would be greatly appreciated.

I have my laptop with a 60gb HD which I wanted to dual boot with XP and ubuntu.

now I have it set up and everything is fine except it is a bit lop sided.

the xp partition has about 15gb of space with the remainin going to ubuntu.

I know that I could just reinstall  and start again to even out the storage space but what I was hoping to do (and hoping someone can help me) is create a third partition of say about 20gb from the ubuntu partition free space and create a third partition that could be used by both XP and ubuntu.

I hope I have explained this clearly and to note I am using Ubuntu gutsy gibbon

Thanks for your time

---

### Post by Lord_Dicranius on 2007-12-22
Look into [GParted](http://gparted.sourceforge.net/).  It's in the repositories, and you can install with:
```
sudo apt-get install gparted
```
or you can download the LiveCD or LiveUSB image and do it that way :)

---

### Post by happymellon on 2007-12-22
> **Lord_Dicranius said:**
> Look into [GParted](http://gparted.sourceforge.net/).  It's in the repositories, and you can install with:
[code]sudo apt-get install gparted[/url]
or you can download the LiveCD or LiveUSB image and do it that way :)

One thing that should probably be mentioned, make sure you make a FAT / FAT32 / NTFS partition, otherwise Windows won't pick it up.

---

### Post by gredawarha on 2007-12-22
Thanks

 I tried to get gparted but no such luck

I get 

darren@darren-laptop:~$ sudo apt-get install gparted
[sudo] password for darren:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gparted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gparted has no installation candidate
darren@darren-laptop:~$ 

My basic knowledge suggests that I need another repository????

Any idea?

---

### Post by eternicode on 2007-12-22
> **Lord_Dicranius said:**
> It's in the repositories, and you can install with...

Erm....you can't work on a mounted partition...and you can't unmount Ubuntu's root partition without shutting down Ubuntu...

Best bet would be to download a LiveCD distro (my personal fave for a temporary, partition-independent linux shell is [System Rescue CD]("http://www.sysresccd.org/Main_Page")), burn it to disk, and boot from that.  SysRescCD already has ntfs-3g (for NTFS work) and gparted installed, and it has a desktop environment (that has proven buggy on certain systems) that you can launch from the command line (startx)

---

### Post by gredawarha on 2007-12-22
ok i have managed to get gparted and im currently repartitioning the drive.  If i want to be able to access the partition with bothe xp and ubuntu do i need to make sure its FAT32 or can I go with ntfs?

---

### Post by eternicode on 2007-12-22
Best to go with FAT32 for cross-platform access.  NTFS read/write support under linux is still unofficial, available by using ntfs-3g.

---

### Post by gredawarha on 2007-12-22
ok FAT32 it is im going to see what happens many thanks

---

### Post by gredawarha on 2007-12-22
many thanks for everyones help know have exactly what i wanted:)

---

