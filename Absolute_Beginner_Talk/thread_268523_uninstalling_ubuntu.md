---
title: "uninstalling ubuntu?"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by jesus of suburbia on 2006-09-30
How can I safely remove ubuntu and kubuntu from my computer. I am worried that if i delete my ubuntu and kubuntu partitions (getting rid of them!) i will not be able to boot up into windows. So how can i remove it without causing any harm to windows? ps i was thinking about it cause of GRUB and the mbr!!!

---

### Post by jesus of suburbia on 2006-09-30
please help this is really needed

---

### Post by pay on 2006-09-30
Format them and then put your windows cd in and boot from it, enter recovery console and type fix boot and fix mbr (maybe its fixboot, fixmbr, its been awhile) and then that will get you back to the windows booloader.

---

### Post by xpod on 2006-09-30
You should be able to just boot to windows and got to disk management to remove the ubunto partitions.
The grub will still allow you to boot to windows ok as far as i know but you could then use your xp cd to "fixmbr" or i even use a bootdisk with fdisk to fix my mbr...you need to be carefull with the latter apparently

---

### Post by jesus of suburbia on 2006-09-30
are you saying that if idelete the linux parts. i will have to sort of reinstall windows? will it bugger up my mbr? you see i dont have my windows CD

---

### Post by jesus of suburbia on 2006-09-30
anyone?

---

### Post by xpod on 2006-09-30
Patience pal:D 

I dont have xp cd`s either mate.
I somehow install and fix my xp quite ok....sometimes:confused: ;) 

Download a 98 bootdisk or something similar that has "fdisk" on it or get the "fixmbr" utility on to it.

You wont have to re-install windows other than fixing the mbr but you should still be able to boot to it ok without it......i think?

---

### Post by pay on 2006-09-30
But the grub config files are on the same partition as ubuntu are they not? So deleting the Ubuntu partitions will mean that you can't config grub or maybe cant use it at all:confused: If you have a 64bit cpu then you can legally download a 6 month trial cd for win xp x64 pro from the microsoft site and use that to fix the mbr.
EDIT: Just realised you don't have a 64bit cpu.

---

### Post by thephantomlinguist on 2006-09-30
Here you go, step-by-step:

1. Boot into windows
2. Go to bootdisk.com and download the Win98 custom disk.
3. Pop a clean floppy into your drive and run the program you downloaded--it'll drop a boot image onto your floppy with the utilities you need.
4. Reboot with the floppy.
5. When it boots, it'll give you a command line. Type
```
fdisk /mbr
```
6. Reboot (after removing the floppy)

You shouldn't see GRUB or anything. It'll just boot straight into Windows.

Once you're in Windows, right-click on My Computer and choose Manage

Find Disk Management (or something like that--I'm doing this from memory right now) on the left-hand side.

Find each of your Linux partitions, right-click and choose delete partition. Once you've deleted them all, you can make one big partition or do whatever you want with them.

It may also be possible to run 'fdisk /mbr' from a command prompt inside Windows, but I'm not sure.

Hope this helps!

---

### Post by xpod on 2006-09-30
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

EDIT:not sure if link is ok:confused:

---

### Post by pay on 2006-09-30
The link worked for me.

---

### Post by xpod on 2006-09-30
I was trying it myself once id posted it but i was getting some "cant display page" nonesense......??
Its fine now...good stuff!
Hope you`se are`nt getting rid for good?:confused:

---

