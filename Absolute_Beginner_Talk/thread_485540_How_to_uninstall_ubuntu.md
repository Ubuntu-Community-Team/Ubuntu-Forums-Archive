---
title: "How to uninstall ubuntu"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by ringorulesall on 2007-06-27
I have a dual boot setup with windows xp on my laptop. I have a limited amount of space so I decided to put ubuntu on my desktop instead. Unfortunately I dont know how to get rid of ubuntu off my laptop while keeping xp intact. 

I tried formatting the Linux partition and swap file, I restarted and got where it would ask me whether i wanted to boot into ubuntu or windows and it said "Error 22" and wouldn't go any further. So i reloaded Ubuntu and now im back to square one.

Any suggestions?

---

### Post by ugm6hr on 2007-06-27
In Windows XP - you need to boot from the XP disc, and go into recovery mode (I think you press R) - then use the fixmbr command.  You can just search for fixmbr in this forum for lots more details.

In Windows Vista - you need to use EasyBCD:
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

The empty space previously ossupied by Ubuntu will still be empty - until you repartition / format.

---

### Post by molly_001 on 2007-06-27
Back up your important data, of course, from the NTFS partition (Windows flavor).

Now use GParted LiveCD, to delete the ext3 partition(s) as well as the swap partition.  Sounds like you probably already use GParted LiveCD there.

At this time, you'll have a smaller-than-desired NTFS partition size, with blank unallocated free space behind it.

Then, resize the NTFS partition to make it larger as desired.

%%%

Now use a Windows installation CD -- not a restore CD, but an installation CD.
Boot from that CD.  Follow its directions as if you were going to install XP, but  choose the 'Repair' option.  It will reinstall XP in C:\Windows, without touching your personal files, and it will overwrite the MBR to boot into Windows.

Another option would be to do all before '%%%' above ... then just use the bootable CD of GAG Boot Manager.  It will give you an iconic menu (press the 'Flying Windows' to boot into Windows flavor...)

GAG is very good for this.

-----
fixmbr in Recovery Console (boot from Win install CD) as he has written will do the trick.  Just don't forget to delete and resize NTFS as he mentioned.

---

### Post by ringorulesall on 2007-06-27
Thank you so much for your help! I love how fast responses are on this forum.

---

