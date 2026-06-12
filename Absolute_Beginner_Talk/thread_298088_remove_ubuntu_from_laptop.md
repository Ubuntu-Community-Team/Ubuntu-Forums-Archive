---
title: "remove ubuntu from laptop"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by maneesh77 on 2006-11-12
I had Xp on my laptop, then I installed ubuntu on it(duel os grub). Is there a way to remove it without deleting xp from the hard disk??

---

### Post by Jareth on 2006-11-12
What I did was run the live CD and go into the Gnome partition manager under System>Administration

I just deleted the ubuntu partition and increased my Win98 partition. That got rid of the Grub for me too. I did however end up formating the lot, but I can't remember why? I think it was just to clean instal my win98 partition cos it had lots of junk on it, rather than any problems with it running.

---

### Post by bulldog on 2006-11-12
You can boot XP and go to disk management.
Delete the partitions which where used by ubuntu and make new partitions for windows and format them.

To remove GRUB from your MBR,fire up the windows install disk and go to recovery console.

Then ```
fixmbr  and/or fixboot
``` reboot, and all should be windows minded again.:D

---

### Post by maneesh77 on 2006-11-12
So basically save my data and format the HD.

Well that's the easiest was, but I was hoping I won't have to do anything to the XP.

---

### Post by bulldog on 2006-11-12
> **maneesh77 said:**
> So basically save my data and format the HD.

Well that's the easiest was, but I was hoping I won't have to do anything to the XP.

Nope, you don't have to format the whole hdd,only the ubuntu parts.

Let the windows partition as it is and just use the disc to recover your MBR.

---

### Post by webjames on 2006-11-12
if you use XP's disk management utitity you can get a nice overview of what is going on with your hard drives.
access this by clicking:
START>CONTROL PANEL>ADMINISTRATIVE TOOLS>COMPUTER MANAGEMNT

then from there click 'disk management'

hope this help, you can format and make/delete partitions from there.

NOTE: this might only be available on XP Professional 

Regards, James

---

### Post by maneesh77 on 2006-11-12
alright, will give it a try thanks

---

