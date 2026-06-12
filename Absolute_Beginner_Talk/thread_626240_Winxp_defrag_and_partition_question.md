---
title: "Winxp defrag and partition question"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by BlocknBleed on 2007-11-28
I'm having some trouble defragging my windows drive to prep it for a possible linux install. 
Right now I'm dual boot with 2 80Gb hard drives, WinXP on one Ubuntu 6.06 on the other. I was going to replace dapper with 7.10 but I also want to clear room on my windows drive(which is only about 30% full) to experiment with other distros. 

The problem is this:[ATTACH]51753[/ATTACH]
My C: drive refuses to defrag anymore than this and I'm afraid if I repartition it I'll lose whatever data is in that rogue little block near the end. 

Also, if all goes well are there any brilliant ideas on how to go about this so I could keep XP and play around with 2 linux distros? 
Here's my setup onthe other HDD. The 2Gb FAT was so I could share files with windows.
[ATTACH]51754[/ATTACH]

---

### Post by dward526 on 2007-11-28
Although the theory goes that you should defrag before partitioning, and this is good practice, I have done successful partitioning without a successful defrag.

I would strongly recommend backing up all important data first, however.  Errors in partitioning can ruin your day quickly without backups.

GRUB should continue to recognize XP and your Linux distros after you install the second one.  I have no personal experience with this however, but the theory is sound.

---

### Post by BlocknBleed on 2007-11-28
So cross my fingers and hope for the best. lol
I'll give it a try.
I'm more afraid of ruining Ubuntu than windows. I just haven't had the best luck with Wine to skid windows completely. MS still has me by the short and curlies.
Thanks for the reply

---

### Post by dward526 on 2007-11-28
Thats about it ;), side note...set up a virtual machine on your Linux box using Innotek VirtualBox, install XP into it, and then network it to your host machine...run all your Microsoft apps in the VM.  

Stick it to the man :)

---

### Post by Sef on 2007-11-29
> I was going to replace dapper with 7.10

If you want another stable version, wait till April 08 when Hardy Heron comes out.

---

