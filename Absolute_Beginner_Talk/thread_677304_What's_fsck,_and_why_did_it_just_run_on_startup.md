---
title: "What's fsck, and why did it just run on startup?"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by kanati on 2008-01-24
I went to boot up my computer today and all was normal until I got to the Ubuntu splash screen (prior to login).  I got a screen with a warning saying:

fsck 1.40.2  (12 - Jul - 2007)
/dev/sdb1 has been mounted 33 times without being checked, check forced

It ran a quick scan (about a minute or two) and then booted into ubuntu as normal.  Nothing seems to be wrong with the system otherwise.  Is this just a regular maintenance thing or should I be worried?   I'm using Ubuntu 7.10 and this is the first time I've ever seen that warning.

Thanks

---

### Post by roachk71 on 2008-01-24
This is the regular filesystem check, and unless **fsck** has to fix any errors, is nothing to worry about.

If you were to use XFS as your filesystem, there wouldn't be an automatic check, but XFS doesn't take power outages well.

The interval between automatic checks can be set using **sudo tune2fs -c {number of mounts between checks} /dev/hdb1**, and the -C option can set the current mount count. These can also be used together.

It's generally ill-advised to use this on a mounted filesystem, but I've gotten away with it countless times...:mrgreen:

---

### Post by Lord Illidan on 2008-01-24
fsck is a program that checks your file systems. Ubuntu is configured to run this program every 30 boots. You can disable this feature if you want, though.

---

### Post by philinux on 2008-01-24
Dear Ubuntu Master Roaster,

Is it true or false that ext3 file systems with their journal do not need fsck?

---

### Post by articpenguin on 2008-01-24
> **philinux said:**
> Dear Ubuntu Master Roaster,

Is it true or false that ext3 file systems with their journal do not need fsck?


   You  should  strongly  consider  the  consequences  of disabling
              mount-count-dependent  checking  entirely.   Bad  disk   drives,
              cables,  memory,  and kernel bugs could all corrupt a filesystem
              without marking the filesystem dirty or in error.   If  you  are
              using  journaling on your filesystem, your filesystem will never
              be marked dirty, so it will not normally be checked.  A filesys&#8208;
              tem error detected by the kernel will still force an fsck on the
              next reboot, but it may already be too late to prevent data loss
              at that point.

from tune2fs

---

### Post by articpenguin on 2008-01-24
also jfs and reiserfs dont have a time check either.

---

### Post by Kilz on 2008-01-24
[You could use Autofsk]("https://wiki.ubuntu.com/AutoFsck") to change the fsck check from bootup to shutdown. Then the check can run while you go away from the computer instead of when you want to use it.

---

### Post by philinux on 2008-01-24
> **articpenguin said:**
> You  should  strongly  consider  the  consequences  of disabling
              mount-count-dependent  checking  entirely.   Bad  disk   drives,
              cables,  memory,  and kernel bugs could all corrupt a filesystem
              without marking the filesystem dirty or in error.   If  you  are
              using  journaling on your filesystem, your filesystem will never
              be marked dirty, so it will not normally be checked.  A filesys&#8208;
              tem error detected by the kernel will still force an fsck on the
              next reboot, but it may already be too late to prevent data loss
              at that point.

from tune2fs

The question was addressed to the ubuntu master roaster.

I have it enabled at 50 boots.

---

### Post by stickx911 on 2008-01-24
> **roachk71 said:**
> This is the regular filesystem check, and unless **fsck** has to fix any errors, is nothing to worry about.

If you were to use XFS as your filesystem, there wouldn't be an automatic check, but XFS doesn't take power outages well.

The interval between automatic checks can be set using **sudo tune2fs -c {number of mounts between checks} /dev/hdb1**, and the -C option can set the current mount count. These can also be used together.

It's generally ill-advised to use this on a mounted filesystem, but I've gotten away with it countless times...:mrgreen:

How do you run it manually? So I can do it when I have time, and so I don't have to wait 15 min. when I need the computer to boot "now".

---

### Post by Kilz on 2008-01-24
> **stickx911 said:**
> How do you run it manually? So I can do it when I have time, and so I don't have to wait 15 min. when I need the computer to boot "now".

The link in my post number 7 also has an option to choose when the scan is run.

---

### Post by kanati on 2008-01-24
thanks for the info, just glad it's nothing to worry about, I can live with an extra 2 minutes once every 30 boots

---

### Post by Lord Illidan on 2008-01-25
> **philinux said:**
> The question was addressed to the ubuntu master roaster.

I have it enabled at 50 boots.

Anyone can answer questions here, and he answered your question correctly. For more information : [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

---

### Post by articpenguin on 2008-01-25
> **stickx911 said:**
> How do you run it manually? So I can do it when I have time, and so I don't have to wait 15 min. when I need the computer to boot "now".

you can do 
> sudo touch /forcefsck

that will force fsck on the next boot up. Dont ever run fsck on a mounted volume.

---

### Post by Vadi on 2008-01-25
There's a great program AutoFsck that will warn you when you shutdown, if your fsck is due or no. You also have the option of delaying it right there.

[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

---

