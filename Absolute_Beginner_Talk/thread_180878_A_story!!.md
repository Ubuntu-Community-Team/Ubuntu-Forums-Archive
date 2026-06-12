---
title: "A story!!"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by mevan on 2006-05-23
One of my PCs has WindowsXP and Ubuntu installed, on different hard drives. I am using fuse to access my NTFS drive under Ubuntu, and till last week everything was working fine. But suddenly Ubuntu at each boot-up started writing something like "block access error ###### on sda1" (my NTFS drive) but continued to boot and work properly.. So did Windows, their disk check utility stated that there was no problem, and I started blaming fuse....

Till yesterday. Windows crashed, and a manufacturer's (seagate) chacking utility found a bunch of bad sectors on the NTFS drive!!!! 

My point is that linux, although on a different drive knew it a week ago!! And windows couldn't tell that their native drive was slowly and inevitably dying!!! (I am in the computer business for years, windows indeed have a very decent disk checking subsystem). 

So, it is just strange and -apart from the lost data- funny!

---

### Post by Sef on 2006-05-23
> My point is that linux, although on a different drive knew it a week ago!! And windows couldn't tell that their native drive was slowly and inevitably dying!!! (I am in the computer business for years, windows indeed have a very decent disk checking subsystem).

Obviously Windows has a blind spot somewhere.  Would be interesting to know where it is exactly, so others won't suffer the same fate as you.  (I do hope that you can recover at least some, if not all of your data.)

---

### Post by it.henrik on 2006-05-23
I hope you made backups ;)

---

### Post by mevan on 2006-05-23
A possibility is that the "blind spot" has to do with the SATA controller driver and specifically with a recent upgrade "windows update" performed to it (Silicon Image 3114I, i cannot remember version of update)... 
Untill that specific update chkdsk (windows disk check utility) performed OK. After the update, chkdsk kept finding file system errors, but it stated that they were successfuly corrected. 
Of course the above could be a coincidence and at the end just a weird HDD fault....


Luckily, I had some backups. Most of my data is recovered now:)

---

