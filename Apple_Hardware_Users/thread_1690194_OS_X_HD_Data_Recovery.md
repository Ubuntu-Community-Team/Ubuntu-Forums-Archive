---
title: "OS X HD Data Recovery?"
date: 2011-02-18
forum: Apple Hardware Users
---

### Post by bug67 on 2011-02-18
I booted up the ol' PowerPC (Ubuntu is default) and was confronted with a pop-up that said the OS X HD was in Imminent failure.  

I can see all the OS X files from in Nautilus in Ubuntu.  However, when I go to drag and drop I am served notice that I do not have sufficient permission to do so.

How do I gain said permissions?  I tried opening them with gksu nautilus "open as administrator but, it didn't work.

Any help would be greatly appreciated.

---

### Post by linuxopjemac on 2011-02-18
[http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=95](http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=95)

---

### Post by Bucky Ball on 2011-02-18
Open a terminal and:

```
gksudo nautilus
```

That should give permission to drag and drop.

Careful what you are doing though as you have Nautilus open as root. ;)

---

### Post by Hatsune Miku on 2011-02-19
> **bug67 said:**
> I booted up the ol' PowerPC (Ubuntu is default) and was confronted with a pop-up that said the OS X HD was in Imminent failure.  

I can see all the OS X files from in Nautilus in Ubuntu.  However, when I go to drag and drop I am served notice that I do not have sufficient permission to do so.

How do I gain said permissions?  I tried opening them with gksu nautilus "open as administrator but, it didn't work.

Any help would be greatly appreciated.

When copying over the files, Make sure you copy them over to a Filesystem that doesn't use POSIX/UNIX file permissions! So you can take OS X's file permissions off, then copy them over to your GNU/Linux Partition.

Examples: Fat32/Fat64 and NTFS.

---

### Post by bug67 on 2011-02-19
> **Hatsune Miku said:**
> When copying over the files, Make sure you copy them over to a Filesystem that doesn't use POSIX/UNIX file permissions! So you can take OS X's file permissions off, then copy them over to your GNU/Linux Partition.

Examples: Fat32/Fat64 and NTFS.

I have no idea what any of that means.  :oops:

I have The computer booted to Ubuntu which resides on one internal hard drive.  OS X resides on the other (borked but able to be seen in nautilus) internal hard drive.  I want to drag the file from my user folder on the OS X drive to an *external* hard drive.  I can drag and drop *some* of the files from the OS X drive to the external but some of them (the important ones like my iTunes folder and such) have big X's on them and I'm told I don't have permission to move them.

---

### Post by Hatsune Miku on 2011-02-19
> **bug67 said:**
> I have no idea what any of that means.  :oops:

I have The computer booted to Ubuntu which resides on one internal hard drive.  OS X resides on the other (borked but able to be seen in nautilus) internal hard drive.  I want to drag the file from my user folder on the OS X drive to an *external* hard drive.  I can drag and drop *some* of the files from the OS X drive to the external but some of them (the important ones like my iTunes folder and such) have big X's on them and I'm told I don't have permission to move them.

1. Make sure your Removable HDD is formatted NTFS, Fat32 or Fat64
2. Open terminal, type in sudo nautilus
3. in the window that just popped up drag the User folder from OS X to the drive
4. once everything is done copying either put it on your Ubuntu driver or leave it on the backup.

---

### Post by Bucky Ball on 2011-02-19
> **Hatsune Miku said:**
> 
2. Open terminal, type in sudo nautilus


gksudo nautilus. gksudo to open anything outside the terminal (like a gui).

---

### Post by bug67 on 2011-02-20
Thanks everybody.  Got it all swapped over.  Whew!

I think where I was running into problems is, I was trying to open up the wrong folder.  Anyhow, it appears to be sorted.

By the way, I had all my data backed up elsewhere so, this wasn't a *huge* deal.

Thanks!

---

### Post by alicesmith on 2011-04-30
hii 
Dont worry I faced the similar situation. Mac OS X is efficient operating system but data loss situation may occur in Mac system there are many reasons that leads to loss of data.
In the case you have no backup of data available, you can use third party application software to recover lost data.
All the best

---

