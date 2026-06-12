---
title: "Triple boot Vista, XP, Ubuntu; XP not working ''NTLDR missing''"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by B.A.L. on 2007-09-29
Hi there!

First I just wanna say I'm new to Linux/Ubuntu, and thus also to this forum, so hi!

Anyway, my problem:
Because I don't want to dive into Ubuntu right away, and because I still haven't made up my mind about Vista or XP, I want to triple boot my laptop, using grub to boot into either of the 3. Now, Ubuntu and Vista are already working, after installing Ubuntu Vista showed up in Grub, working fine. XP however didn't show up, altough it is normally installed on a partition. If I manually add Grub's menu.lst inserting an entry for Windows XP referring to the partition it installed on, I get the famous ''ntldr missing'' error. By the way, the partions are:

1: Vista
2: XP
3: Linux
4: extended (linux swap)

I think the problem is that Windows XP always wants to boot from the first partion, even tough XP itself might be on the second...and because GRUB goes directly to the second partition, XP can't boot...so, how I see this can be solved:

1: Just skip ntldr and let Grub load XP itself
2: Let Grub go trough partition 1 to partition 2...

Also, ''fixmbr'' from the XP CD doesn't work, the ntldr error stays

O yeah, btw, when I just boot up Vista it doesn't mention XP anywhere in the booting section, while it does see XP's drive...

If anyone knows how to solve this, please let me know...there must be some way to get around this problem, and its probably easy, I just dont know how :P

---

### Post by amonrath on 2007-09-30
[QUOTE=B.A.L.;3446578]Hi there!

i've got the same as you bud but yep you got2 have xp 1st then vista so it's loader pickzup xp as "earlier windows version then ubuntu as it's grub pickzup all of themup i manually partitiond the 80 and manually installed my feisty as i was'nt interested in it's guided blah blah, i used paragon partition mananger as  it formats linux aswel as windows, i'm like you bud don't know jack bout linux or it's terminology it took me weeks to figure out just how to get beryl up n running and finally got my desktop to "rain" a water pond effect and to have my windows catch on fire other than that i'm still a dummy

---

### Post by B.A.L. on 2007-10-01
Uhm...thanks, but I don't really get your comment. :P Does anyone else know how to fix this?

---

### Post by Ozeuss on 2007-10-01
> **B.A.L. said:**
> Hi there!
Because I don't want to dive into Ubuntu right away, and because I still haven't made up my mind about Vista or XP, I want to triple boot my laptop, using grub to boot into either of the 3. Now, Ubuntu and Vista are already working, after installing Ubuntu Vista showed up in Grub, working fine. XP however didn't show up, altough it is normally installed on a partition. If I manually add Grub's menu.lst inserting an entry for Windows XP referring to the partition it installed on, I get the famous ''ntldr missing'' error. By the way, the partions are:

1: Vista
2: XP
3: Linux
4: extended (linux swap)

I think the problem is that Windows XP always wants to boot from the first partion, even tough XP itself might be on the second...and because GRUB goes directly to the second partition, XP can't boot...so, how I see this can be solved:

1: Just skip ntldr and let Grub load XP itself
2: Let Grub go trough partition 1 to partition 2...



number 1 should be your choice. how did you add windows xp to grub menu.lst? it should be something like
```
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```
at the end of the file, and root be pointing to your xp partition (if XP is the secondpartition, it is hd(0,1)

---

### Post by B.A.L. on 2007-10-01
Yeah, that's exactly what I did, but then it says NTLDR missing...XP is on the second partition yeah, so I used (hd0,1).

EDIT: Only the title is different, but that can't be the problem can it?

---

### Post by Foxblood on 2007-10-01
I encountered the same problem some time ago. There were two files that I copied from Vista and put in the appropriate place in XP. NTLDR and ntdetect, I think it was. Sorry about not being more precise.

---

### Post by B.A.L. on 2007-10-01
Ok, ive don it, but now when I start XP is get a very brief message saying ''Windows is being started from C:Windows'' (something like that, my OS is in dutch, and then I get a black screen. When I was using the XP partition thingie on the CD it might be that I installed XP on a D:, and it also shows like that in Vista...could that be it? Some more help please? :P

---

### Post by EmmyCee on 2007-10-01
I had a similar problem with my dual boot. It sounds like you're using partitions on the same drive, whereas I was using separate hard drives. I'll bet your boot records in XP are messed up. You might be able to fix it in recovery console, but you may have to reinstall XP.

Just on a personal note, that triple boot sounds horribly masochistic. Good luck to you! :)

---

### Post by B.A.L. on 2007-10-01
Ok, it's fixed!!!

I looked up the booting mechanism of XP and besides NTLDR and NTDETECT it also needs boot.ini to boot up. Now, this is the standard boot.ini:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

And to boot up XP when it's on the 2nd partition you just have to make this boot.ini in the root folder, but then change the partition number into 2.

Thanksa for your help guys, a good first experience with the Ubuntu forums, hope I get into Ubuntu a little bit more, and maybe you'll see me around here more. :P So this is solved now, do I have to communicate this to the mods, or...?

---

### Post by Ozeuss on 2007-10-02
> **B.A.L. said:**
> 
Thanksa for your help guys, a good first experience with the Ubuntu forums, hope I get into Ubuntu a little bit more, and maybe you'll see me around here more. :P So this is solved now, do I have to communicate this to the mods, or...?
Its great to hear. enjoy Ubuntu! you can edit your thread title to mark it [SOLVED], that's about it.

---

