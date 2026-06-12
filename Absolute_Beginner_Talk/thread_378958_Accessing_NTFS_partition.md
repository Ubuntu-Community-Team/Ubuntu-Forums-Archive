---
title: "Accessing NTFS partition"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-03-07
[edit - have just found [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009) so will research that a little, may have answered own q]





I have:

/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda5

/dev/sda3 is a Windows Vista NTFS partition.

Everything else is to do with Ubuntu.

I have successfully broken my Vista installation :) , and could do with accessing the NTFS filesystem on sda3, from within Ubuntu so I can try and fix it.

(I think I've messed up the Vista bootloaders that lie beyond grub, in sda3's root somehow)

Seem to recall being able to access an NTFS partition on someone's XP computer with a live Knoppix CD a few years ago but maybe I am mistaken?

---

### Post by kelbizzle on 2007-03-08
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows) 

There ya go. Just replace /dev/hda1 with /dev/sda3

---

### Post by ecs_pf5 on 2007-04-24
Weird. I was sure I had Windows NTFS  on /dev/sda3

But, it kept giving me errors

So, I tried mounting /dev/sda1

... and all my Windows files turned up in /media/windows

So I guess I'm misunderstanding the order of the partitions somewhere along the line. Anyway, it's working now.. thanks :)

---

