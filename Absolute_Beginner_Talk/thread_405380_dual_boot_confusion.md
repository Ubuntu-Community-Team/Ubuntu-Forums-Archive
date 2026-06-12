---
title: "dual boot confusion"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by bluewagon on 2007-04-09
Ive been searching these threads and saw a dual boot section in the stickies and also searched google, but everytime i go to something to explain to me dual booting it seems like its only for one hard drive, and i wish to use 2 hard drives, one for xp and other for ubuntu. but i can't seem to find the howto for it.. or are all those links the howto for it(but then why do i need to do partitions if im not even going to touch the other hard drive and installing a another one?)
could anyone please give me a guide to using two hard drives

---

### Post by Gina on 2007-04-09
I have two machines set up with diual-booting and with Ubuntu and Windows on different drives.  Just install Ubuntu on a different drive from Windows (either using the whole drive or part of one).  Ubuntu will detect Windows and put the boot menu on the main drive when it installs.  All automatically - once you've chosen where to install Ubuntu and set up new partitions if required.

Hope that answers your question.

---

### Post by orb9220 on 2007-04-09
Yes the secret or confusion people have is installing grub on the same drive as linux.
This is not correct.

You must install grub to the first drive because that is where the bios looks for booting.

So even tho I have xp on hda (hda0,0) and linux on hdb (hdb0,0) as a rough example I would still want grub installed on hda (hda0,0).

---

### Post by antoz on 2007-04-09
there is a lot of info on the link below

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by confused57 on 2007-04-09
> **bluewagon said:**
> Ive been searching these threads and saw a dual boot section in the stickies and also searched google, but everytime i go to something to explain to me dual booting it seems like its only for one hard drive, and i wish to use 2 hard drives, one for xp and other for ubuntu. but i can't seem to find the howto for it.. or are all those links the howto for it(but then why do i need to do partitions if im not even going to touch the other hard drive and installing a another one?)
could anyone please give me a guide to using two hard drives

Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by reality_hunter on 2007-04-10
> **orb9220 said:**
> Yes the secret or confusion people have is installing grub on the same drive as linux.
This is not correct.

You must install grub to the first drive because that is where the bios looks for booting.

So even tho I have xp on hda (hda0,0) and linux on hdb (hdb0,0) as a rough example I would still want grub installed on hda (hda0,0).

Hi, wow you nailed the question I was hoping somebody here can guide me with.  I have similar set....windows installed on slave hard disk and then installed UBUNTU on the master drive.  I know the grub has been loaded into the slave disk because thats where i have to boot from whenever i want to logon to win or UBUNTU.  When I try to boot from the master drive...an error comes up saying no OS found...so ..this is the way it now.
My question is that how can I change the setting, so that I can boot from my master drive instead of the slave drive,.................or better yet CAN I boot from either disk drives and have the boot manager popup?  please help I have gone through a lot of HOWTOs and google as well.
If you know the answer please advice,
thanks

---

### Post by orb9220 on 2007-04-12
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

This link will tell you how to redo grub. You just have to be sure How you want it to boot.

---

### Post by reality_hunter on 2007-04-13
> **orb9220 said:**
> [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

This link will tell you how to redo grub. You just have to be sure How you want it to boot.

thanks orb, will look at this later this month when i finish writing exams. thank you for the reply.

---

