---
title: "[SOLVED] Taking a step backwards..."
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Adbru on 2008-01-31
Hiya,

As part of my "fiddling" around with the system I have tried going back to XP to test I could do it.

I took a ghost image of the XP partition before installing Fluxbutu.

I went for a clean instal rather than dual boot (small hard drive)

I am now at the point where I've used the system rescue cd [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
and used the Gparted tool to delete the linux partitions (both swap and root), then converted the free space into a ntfs partion and formated it as a primary partition. Then used ghost to restore my XP image onto it.

I have done this previously but just with different XP images (lazy backups !)

Problem is that I cant seem to get rid of the grub bootloader !! 

Any help greatfully received 

Thanks in advance

Adbru

---

### Post by jrusso2 on 2008-01-31
[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)

Run fixmbr

---

### Post by arochester on 2008-01-31
There are various ways to fix the MBR - from the Windows disk - from the Ubuntu LiveCD. |For the latter see e.g. [http://www.arsgeek.com/?p=3340](http://www.arsgeek.com/?p=3340)

---

### Post by jan quark on 2008-01-31
If you have the XP CD cd run the recovery console and use the command fixmbr That will rewrite the master boot record for XP

---

### Post by Adbru on 2008-01-31
thanks guys,

i am at work and xp cd is at home :( so currently booting my 7.04 live cd to try it that way.

I'll let you know how it goes ......

Thanks again

Adbru

---

### Post by Adbru on 2008-01-31
Hello again,

Seems to be the night for Grub questions :confused:

Well I've tried using ms-sys from the live-cd (7.04), I've hit it with big sticks, i've offered it money but still cant get rid of the grub loader !!

Think I'll give up for tonight and try it with the XP recovery disk in the morning when i get home. 

Thanks for the help earlier, i will get to the bottom of this eventually. 

Adbru

---

### Post by Adbru on 2008-02-01
Hi Guys,

Got it sorted :)

We have a copy of ERD Commander at work so used that and I am now back to Billyware :(

Thanks for your help earlier.

Adbru

---

