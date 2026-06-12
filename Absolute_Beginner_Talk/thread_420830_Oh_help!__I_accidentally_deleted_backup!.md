---
title: "Oh help!  I accidentally deleted backup!"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Gen2ly on 2007-04-24
For heavens sake.  I'm not sure what I did but... I wanted to try Fiesty Fawn so I backed up my other linux distro before installing.  Now all thats left is a 1k file that has its name.  I'm not sure what happened but I suppose all there is left to do is try a data recovery program?  I have alot of things in that backup that I need.  Anyone heard of something that can do this well?

---

### Post by amohanty on 2007-04-24
> so I backed up my other linux distro before installing

How and where?
Whats your partition layout?

> I wanted to try Fiesty Fawn

Did you install it or just try the live cd version?

---

### Post by marko_4454 on 2007-04-24
Remember that if you used the terminal for removing anything, ie, "rm" command. Then there is no coming back...its well, gone.

---

### Post by Gen2ly on 2007-04-24
> **amohanty said:**
> How and where?
Whats your partition layout?

Appreciate the helps.

here's the line I used from /

```
tar cvpzf /mnt/Shared-Disk/Storage/Backups/MacBook-Gentoo.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```

Worked nice when I use Ubuntu before.

/mnt/Shared-Disk I haven't touched since I did this except to right-click and check it's size (which seemed correct [6.8 GB]), and mounted in Feisty Fawn.  I have not saved anything to it!

> Did you install it or just try the live cd version?

I installed the os with the live cd  (Like it a lot thus far).   The problem however has no relation to Feisty Fawn as I cannot not see it from the Other LiveCD's.

---

### Post by gradedcheese on 2007-04-24
This 'backup', did you do it while booted into the OS you were backing up?  If so, I find that kind of weird, 'not sure that it would work well.  Perhaps the backup file was always 0kb?  Did you do it as root?

Check the size using the shell to be (more) sure:

```

du -h /media/disk/Storage/Backups/MacBook-Gentoo.tgz

```

---

### Post by Gen2ly on 2007-04-24
> **gradedcheese said:**
> This 'backup', did you do it while booted into the OS you were backing up?  If so, I find that kind of weird, 'not sure that it would work well.  Perhaps the backup file was always 0kb?  Did you do it as root?

Check the size using the shell to be (more) sure:

```

du -h /media/disk/Storage/Backups/MacBook-Gentoo.tgz

```

Obliged thanks.  Yes this is definitely weird.  I remember specifically right-clicking the tarred file and seeing 6.8 GB..  I opened it also with File Archiver (aka file-roler) and did a fast scan of the directory before leaving Gentoo.  My thought, though far fetched, is that a hacker  hacked in while I was installing Feisty Fawn (the Live CD isn't that secure.)  Sigh.  Heres the result of when I "du -h" the file:

```
0       /media/disk/Storage/Backups/MacBook-Gentoo.tgz
```

---

### Post by gradedcheese on 2007-04-24
What sort of disk is /media/disk?  It's common for files to not be written to USB disks (for example) until you unmount them, collecting all writes/deletes into one  big operation (it's useful for Flash disks).  Perhaps you 'wrote' to it but never unmounted?  You can force a write-out with "sudo sync" in these cases,  Sounds like your backup is indeed gone though :(

---

### Post by amohanty on 2007-04-25
Also when you installed fiesty, did you repartition your hdd's?

Did you format the HDD on which you had gentoo?

Is /media/disk a USB HDD?

AM

---

### Post by akudewan on 2007-04-25
If your data is really gone, you can try PhotoRec to recover it: [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

(It does more than just photos, the name is misleading)

---

