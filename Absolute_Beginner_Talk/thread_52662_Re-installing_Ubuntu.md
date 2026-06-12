---
title: "Re-installing Ubuntu"
date: 2005-07-28
forum: Absolute Beginner Talk
---

### Post by bk452 on 2005-07-28
I'm new to linux and my answer to problems that I can't fix is to reinstall.
How can I recover the space that I've lost from doing this.  I have a dual-boot to windows xp:

IDE 1 Master (hda) - 40.0 GB

#1 Primary          21.0  GB         ntfs
#2 Primary          15.4  GB         ext. 3
#8 Logical         690.0  MB        swap
#7 Logical         723.8  MB        swap
#6 Logical         723.8  MB     
      Logical         723.8  MB        FREE SPACE
#5 Logical         723.8  MB        swap

---

### Post by Juergen on 2005-07-28
> I'm new to linux and my answer to problems that I can't fix is to reinstall.Hm, that's a bit 'Windows'-ish, but as long as you don't know better...

With lost space you mean all those swap-partitions?
You can delete them (NOT the one youre using ATM) with any partitioner.
'cfdisk' is relatively userfriendly.

Or wait till your next re-install and choose 'expert' mode, then you can modify your partitioning before the system is copied.

BTW: Try to create an extra partition for your /home. That way all your configurations won't be lost the next time you install.
Write a log for each modification you do to the system, so maybe you'll be able to avoid the re-install by just reverting that particular change that made the system unstable.
At least, since /home will be there untouched the next time, you can read your log and don't repeat your mistake ;-)

Maybe something like this:
#1 Primary 21.0 GB ntfs
4 logical, rest of availabe space
#5 Logical 8 GB ext. 3, mountpoint / , (probably too big, get experience and size it yourself ;-))
#6 Logical 8 GB ext. 3, mountpoint /home (don't format the next time you re-install)
#7 Logical 723.8 MB swap

Later you might even want to create extra prtitions for other parts of the system (e.g. like /var)

---

### Post by zaal on 2005-07-28
first better know which os is of more priority.linux is way less heavier than win
 \\:D/  \\:D/

---

### Post by bk452 on 2005-07-28
[QUOTE=Juergen]Hm, that's a bit 'Windows'-ish, but as long as you don't know better...

With lost space you mean all those swap-partitions?
You can delete them (NOT the one youre using ATM) with any partitioner.
'cfdisk' is relatively userfriendly.

Or wait till your next re-install and choose 'expert' mode, then you can modify your partitioning before the system is copied.

BTW: Try to create an extra partition for your /home. That way all your configurations won't be lost the next time you install.
Write a log for each modification you do to the system, so maybe you'll be able to avoid the re-install by just reverting that particular change that made the system unstable.
At least, since /home will be there untouched the next time, you can read your log and don't repeat your mistake ;-)

Maybe something like this:
#1 Primary 21.0 GB ntfs
4 logical, rest of availabe space
#5 Logical 8 GB ext. 3, mountpoint / , (probably too big, get experience and size it yourself ;-))
#6 Logical 8 GB ext. 3, mountpoint /home (don't format the next time you re-install)
#7 Logical 723.8 MB swap

Later you might even want to create extra prtitions for other parts of the system (e.g. like /var)[/QUOTE]
 Thanks for the info and yes, I'm a windows refugee.  I'll try 'cfdisk'.  I think I'm too new to try to make a partition for my home, but I'll keep the info for reference when I get some more experience.  Thanks.

---

### Post by bk452 on 2005-07-28
[QUOTE=zaal]first better know which os is of more priority.linux is way less heavier than win
 \\:D/  \\:D/[/QUOTE]
 Linux is far superior to windows and that's a fact.  But I'm a videographer and editor and so far I can't find what I need in Linux.  I've tried Kino, which is good, Cinelerra, which is difficult, Lives which is very good, but Pitivi looks the most promising, for me at least. And Pitivi is still being developed.

I hate booting to windows.

---

### Post by mattiouk on 2005-07-29
I've decided to take the reinstall option after too many problems with a usb keyboard and passwords  ](*,) !

When I reinstall will I need to reinstall the boot manager - GRUB?  Or leave it? Or what??  Sorry, very new here and in need of help!

Matt

---

### Post by poofyhairguy on 2005-07-29
[QUOTE=mattiouk]

When I reinstall will I need to reinstall the boot manager - GRUB?  Or leave it? Or what??  Sorry, very new here and in need of help!

Matt[/QUOTE]

I would let the reinstall CD redo it.

---

