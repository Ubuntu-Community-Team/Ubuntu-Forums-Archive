---
title: "[SOLVED] Truecrypt takes FOREVER to prepare encrypted volume..."
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by drewster1829 on 2008-03-13
I'm running Ubuntu 7.10, upgraded from 7.04, and I was trying to add a 240 GB or so encrypted container on a 500 GB Lacie external USB 2.0 HD (formatted NTFS) using TrueCrypt 5.1.  I'm using AES-256, with SHA-512 for the hash, and a 25 character password.  I used the GUI for TrueCypt, and selected "None" for partition type of the encrypted container (instead of FAT).

I started it last night, and on the 'Volume Format' display, it started at about 12 MB/sec, and an estimated time remaining of about 5 hours.  This morning, (about 12 hours later), it's now at 1.9 MB/sec, with at estimated time of 23 hours.

If I fire up system monitor, mount.ntfs-3g is using 70-80% of CPU, while TrueCrypt is using about 1%.  Last night when I checked, it was probably 60% for mount.ntfs-3g, and 15% or so for TrueCrypt.

II'm doing this on a two year old Toshiba Satellite laptop, 1.73 GHz Pentium M, 512 MB of RAM (showing 70% usage right now).

Now (of course after I started this) I've read about the problems some users have had with ntfs-3g, the Gutsy kernel, and TrueCrypt causing hangs when transferring files to the volume, but I'm wondering if it's normal to take such a long time to actually create the encrypted volume on an NTFS external drive in Ubuntu?  Of course, it IS 240 GB, but still...

I would reformat the drive to ext3, but I don't have enough room on my other drives to transfer all the files off of it.  This was a compromise (by freeing up half the free space on the 500 GB drive,completely filling up two 80 GB drives) which would theoretically only require two containers, but I didn't know about the ntfs-3g, Gutsy, TrueCrypt bug until now.  Maybe I'll just have to buy *another* 500 GB drive and format it ext 3 and start over...but not if it's going to take a week to format it!

---

### Post by wieman01 on 2008-03-13
Encryption rates can go up & down at random, I made the same experience. A 120 GB drive took around 5 hours, so it does not surprise me to hear that yours took over a day, or even more. Formating is really slow.

Mine went from 12 MB/sec down to roughly 500 KB/sec and then up again to approx. 1.5 MB/sec.

---

### Post by drewster1829 on 2008-03-13
> **wieman01 said:**
> Encryption rates can go up & down at random, I made the same experience. A 120 GB drive took around 5 hours, so it does not surprise me to hear that yours took over a day, or even more. Formating is really slow.

Thanks for the reply!  I'm glad to know it's supposed to take this long.  If I had thought ahead I would've done it on my desktop (which is older than my laptop, but it's still faster..Pentium 4), but I have it dismantled to get ready to move.  Anyway, thanks for your help!

---

### Post by wieman01 on 2008-03-13
Another confirmation from a friend of mine who uses Windows... same there. Encryption is a very tedious process if you do it right. But look at the bright side: You only do it once. :-)

---

### Post by justleen on 2008-03-13
Using Safeguard Easy (Windows) encrypting a 25GB partition takes about 5 hours.. So yea, i can image taking a day for your whole drive

---

### Post by hyper_ch on 2008-03-13
well, sudo dd if=/dev/urandom of=/dev/sdX on my SATA II drive (500 GB) took a loooooooooooong time.... I think almost two days or so...

---

### Post by wieman01 on 2008-03-13
> **hyper_ch said:**
> well, sudo dd if=/dev/urandom of=/dev/sdX on my SATA II drive (500 GB) took a loooooooooooong time.... I think almost two days or so...
Wow, my gosh. Isn't time wasted though.

---

### Post by hyper_ch on 2008-03-13
it's not that I had to be standing next to it and couldn't do anything ;)

---

### Post by wieman01 on 2008-03-13
> **hyper_ch said:**
> it's not that I had to be standing next to it and couldn't do anything ;)
Lol... well, some people would certainly prefer it to protect their precious data. Haha...

---

### Post by mrsteveman1 on 2008-03-13
Truecrypt filling the drive with random data is what takes so long, but at least with tc 4.3a it was significantly faster than urandom.

Part of the TC5 troubles I'm sure have to do with the fact that TC5 is no longer a native kernel driver, it is a fuse pseudo-filesystem which exposes the cleartext block device as a loop (/dev/loop0 etc). 

Something you might do tho, if you are going to be filling this encrypted partition anyway after creating it, prefilling it with random data serves no purpose whatsoever, because TC will be overwriting the drive space anyway. So just tell TC to do a quick format etc.

---

### Post by drewster1829 on 2008-03-13
Thanks!  I guess I'll just be patient.

As far as quick format goes, I used the GUI which came with TC 5.1, and on selecting "None" under filesystem type (instead of FAT), the QuickFormat checkbox was greyed out, I think (or maybe I just wasn't clicking on it...lousy touchpad:) ).  Perhaps I should stick with the CLI from now on? :)

I know it's a bad idea to do this w/o backing up the files first, but I'm out of HD space!  Probably 30% of it is backed up on DVD-R, though, so maybe I'll try copying that stuff to the TC partition first, just in case it's not going to work.

Thanks again!

---

### Post by mrsteveman1 on 2008-03-13
Just quick format the TC partition however it wants to format it (vfat etc), mount it, the cleartext device will be /dev/loop0 probably, so you can just execute mkfs.ext3 etc on it. After that it should mount normally.

---

### Post by hyper_ch on 2008-03-14
> **wieman01 said:**
> Lol... well, some people would certainly prefer it to protect their precious data. Haha...

I meant that this drive is my data drive so the OS drive is way smaller and it didn't take that long to format it ;)

---

