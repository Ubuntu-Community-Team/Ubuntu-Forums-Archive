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

### Post by MJN on 2006-05-15
Does the hda5 entry in fstab have a 'errors=remount-ro' option on it? If so, this essentially means that if errors occurs on that partition then it gets mounted as read-only - this is usually done on root partitions to minimise further damage to the file system until you can suss out what's wrong.
 
I very much doubt that hda was actually set to ro in fstab - are you sure you didn't misunderstand the above remount-ro option? Having a read only root won't work.. or rather it'll produce exactly the symptoms you describe.
 
If you can get to a console prompt check what /var/log/boot and /var/log/syslog have to say - you're looking for reasons why hda5 has errors on it (which has led to it being mounted read only).
 
Mathew

---

### Post by cosborn72 on 2006-05-15
I believe it did say errors=remount-ro. That makes a whole lot more sense!

 I am at work now, but I will check the boot and syslogs.

Thanks for your help.

---

### Post by cosborn72 on 2006-05-16
The syslog had stopped recording information as of when the problem started the day before.  I didn't see anything specific in the boot log either.

However, I was able to boot the live CD and then go in and restore my previous fstab, replacing errors=remount-rw with errors remount-ro.  That seems to have fixed the problem.

Thanks for the help!

---

### Post by MJN on 2006-05-16
Ah yes, that's one of the drawbacks with storing your logs /var/logs on the same partition as / - if the latter gets remounted ro then you've lost your logging, and there's every chance that whatever caused the error also prevented the log updating whilst it still had the chance!

Good to hear you're sorted now though, however if you value your data it might be worth running smartctl (from the smartmontools package) on the drive to see if there look to be any SMART errors/problems with it.
 
Mathew

---

