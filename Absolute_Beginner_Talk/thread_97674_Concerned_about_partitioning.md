---
title: "Concerned about partitioning"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by Shadowflare on 2005-12-01
One of the faculty of my schools computer department advised me about partitioning my computer, because after a while it may get 'confused' between what's linux and what's xp (files and programs i assume) which may end up resaulting in my computer malfunctioning and  breaking. Unfourtunatly he doesn't have enough time to get into it with me, so here i am now. What are your opinions on this matter?

  - shadow

---

### Post by Digitallysick on 2005-12-01
i have had my 250 gig hard drive partitioned for several years , dual booting Kubuntu and win xp, never had an issue, tell him that you dont think he knows his Head from his @ss

---

### Post by Kvark on 2005-12-01
Windows and Linux uses different file systems so they will have to use different partitions. Your computer can't get confused over what programs belong to which OS since they don't use the same partition. Besides, even if they could and did use the same partition they can't run eachothers programs, one OS's program is just a random file to the other OS.

---

### Post by az on 2005-12-01
[QUOTE=Shadowflare]after a while it may get 'confused' between what's linux and what's xp (files and programs i assume) which may end up resaulting in my computer malfunctioning and  breaking. [/QUOTE]

The only thing that sounds like it got confused was what was between his chair and his keyboard.

Send him here, we'll straighten him out for you.

---

### Post by Brunellus on 2005-12-01
confusion doesn't exist when one partition doesn't know the other exists (which is the case if you're dual-booting linux and windows).

your instructor doesn't know what he's talking about.

---

### Post by linbetwin on 2005-12-01
Tell your instructor he's a FUDdie-duddie.

---

### Post by wrtrdood on 2005-12-01
Partitioning makes a big physical drive into smaller logical drives.  Sort of like having a bunch of different disk drives all using the same connection.

Windoze cannot natively access partitions that are identified as anything other than the filesystems it knows about (fat, ntfs).  Perhaps this is what he meant.

GNU/Linux, on the other hand, supports (at last count) 95 filesystem types.  No problems here.

One thought comes to mind: if you have installed programs on, say, the D: drive -- then yes -- Windoze will not just get confused, it gets downright angry if you take it away (turn that drive into something like a GNU/Linux filesystem). :D  Registry entries pointing to the old drive (that no longer exists) will drive it nuts and it can be a real pain to fix it without a reinstall.

---

### Post by aysiu on 2005-12-01
What's "the computer"?

The boot loader, if it's Grub, will have menu entries for every operating system, and will know which one is which. The boot loader, if it's Windows', will not recognize Ubuntu but will know which one is Windows.

Windows will see the Ubuntu partition as a "healthy" but unknown partition.

Ubuntu will see the Windows partition as NTFS or FAT32.

Who or what will be confused?

---

### Post by SteelValor on 2005-12-01
exec trying_to_look_smart.cfg

Talk to someone else. He's either biased, clueless or both.

---

### Post by crispingatiesa on 2005-12-01
[QUOTE=aysiu]

Who or what will be confused?[/QUOTE]


The bloke that recommend him not to do it :D

---

