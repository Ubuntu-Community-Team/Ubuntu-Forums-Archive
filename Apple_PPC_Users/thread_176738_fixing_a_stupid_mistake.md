---
title: "fixing a stupid mistake"
date: 2006-05-15
forum: Apple PPC Users
---

### Post by cosborn72 on 2006-05-15
(Note, I am running the newest dapper release, but I don't think that this is a dapper issue, so I'm posting it here instead.)

Maybe someone could help me fix a stupid mistake I made.

I was trying to get MOL to run, and a got an error message saying that hda5 (my main linux partition) was read-only.

I opened Fstab and checked, and sure enough, hda5 was set to ro.  So I changed it to rw.

When I rebooted, the startup stalled while pulling up the x server.

I was able to open a console and log in.  I tried to go back and fix fstab, but when I tried to save the changes, it told me that I can't because the partition is read only.  (Fstab still shows rw under hd5)

When I try to start x, i get several messages saying that the x server was unable to wirte to various files.  For example. 

Server coud not create temp file /home/chris/xAuthority.

Any guesses how i can get back in and fix the problem?

My current configuration is 
hda2 swap
hda 3 OS X
hda 5 Linux (ext2)

---

### Post by tkjacobsen on 2006-05-15
Try to boot into recovery mode(an option in grub). Maybe then you can write to fstab...

If that doesn't work, you could try to boot from a live cd, eg systemrescue: [http://www.sysresccd.org/](http://www.sysresccd.org/) or maby just ubuntu live cd..

---

