---
title: "How to remove unwanted mount points and add new ones?"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by AnotherMuggle on 2007-08-28
How to remove unwanted mount points and add new ones?

I had a triple boot with Vista and want to remove the mount that I had for Vista and create a new mount for the new FAT32 partition.

Thanks.

---

### Post by annda on 2007-08-28
i'd say clean your fstab (remove the vista entry), delete the vista mountpoint from the /media directory, create a new one there for the new partition (preferably in /media too, but it can be anywhere) and save the changes to fstab.

here is a good guide:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

please post back if you have any trouble following the instructions in the guide. good luck!

---

### Post by AnotherMuggle on 2007-08-28
> **annda said:**
> i'd say clean your fstab (remove the vista entry), delete the vista mountpoint from the /media directory, create a new one there for the new partition (preferably in /media too, but it can be anywhere) and save the changes to fstab.

here is a good guide:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

please post back if you have any trouble following the instructions in the guide. good luck!

Thanks.  The problem I am having is that I am denied permission to delete/create directories inside /media.

EDIT: Figured that out lol

---

### Post by trak87 on 2007-08-28
Modifying any directory outside your home directory requires you to become root. At the command line you do this by prepending "sudo" to the command, for example "sudo rm -rf /media/mymountpoint". For GUI use, press Alt-F2 and type "gksudo <program>" to gain root privileges.

---

### Post by glotz on 2007-08-28
> **tomkear2006 said:**
> Thanks.  The problem I am having is that I am denied permission to delete/create directories inside /media.

EDIT: Figured that out lol[[img]http://imgs.xkcd.com/comics/sandwich.png[/img]](http://xkcd.com/149/)

---

