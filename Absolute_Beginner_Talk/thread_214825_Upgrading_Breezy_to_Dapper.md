---
title: "Upgrading Breezy to Dapper"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by brn on 2006-07-13
I have a 2nd hand Dell laptop that came with XP.  I installed Breezy and have Dapper on order.  GRUB came up just like the book said and although Breezy sometimes crashes, it is working right now. (another issue I guess)

When I installed Breezy I patitioned the 20 GB disk like this:

     (boot)  6 GB   ntfs    /media/hda1   (WinXP) 
             4 GB   FAT32   /media/hda2   (Common) 
             4 GB   Ext3    /             (Linux Root)
             4 GB   Ext3    /usr          (linux usr)
             1 GB   Ext3    /home         (Linux home)
            .5 GB   swap    /swap         ('nuff said)
            .5 GB   FAT32   /dos          (*)

From what I have read/heard/hoped, this configuration should let me upgrade without losing the programs and data that are unique to me.  Is it so?

When I installed Breezy I saw no suggestion that it would preserve the content of my partitions.  Did I miss something?   

Thanks,

(*) I really do hope to someday install DOS, I have some nice applications **_*[B]that I wrote***_[/B] and sorely miss.

---

### Post by Radioactive Fellow on 2006-07-13
You can do the [COLOR="DarkSlateBlue"]upgrade[/COLOR], your not going to lose any information stored.

> 5 GB FAT32 /dos

wtf! ;)

---

### Post by richbarna on 2006-07-13
> **brn said:**
> I have a 2nd hand Dell laptop that came with XP.  I installed Breezy and have Dapper on order.  GRUB came up just like the book said and although Breezy sometimes crashes, it is working right now. (another issue I guess)

When I installed Breezy I patitioned the 20 GB disk like this:

     (boot)  6 GB   ntfs    /media/hda1   (WinXP) 
             4 GB   FAT32   /media/hda2   (Common) 
             4 GB   Ext3    /             (Linux Root)
             4 GB   Ext3    /usr          (linux usr)
             1 GB   Ext3    /home         (Linux home)
            .5 GB   swap    /swap         ('nuff said)
            .5 GB   FAT32   /dos          (*)

From what I have read/heard/hoped, this configuration should let me upgrade without losing the programs and data that are unique to me.  Is it so?

When I installed Breezy I saw no suggestion that it would preserve the content of my partitions.  Did I miss something?   

Thanks,

(*) I really do hope to someday install DOS, I have some nice applications **_*[B]that I wrote***_[/B] and sorely miss.

Ok, if you do an upgrade you will not lose your user files as you have placed them on seperate partitions.

The next thing that I have noticed is that unless you have your drive seperated up so much for specific reasons, you are wasting a lot of space.

>       (boot)  6 GB   ntfs    /media/hda1   (WinXP) 
             4 GB   FAT32   /media/hda2   (Common) 
[COLOR=Blue]              4 GB   Ext3    /             (Linux Root)
             4 GB   Ext3    /usr          (linux usr)
             1 GB   Ext3    /home         (Linux home)
            .5 GB   swap    /swap         ('nuff said)[/COLOR]
            .5 GB   FAT32   /dos          (*)

Personally, with so little space, I would back up personal files, and to install Dapper from the cd I would change the partitions that I have marked [COLOR=Blue]blue[/COLOR].

>       (boot)  6 GB   ntfs    /media/hda1   (WinXP) 
              4 GB   FAT32   /media/hda2   (Common) 
[COLOR=Blue]9 GB   Ext3    /             (Linux Root)
512 Mb   swap    /swap [/COLOR]
512 Mb FAT32   /dos          (*)

Some people do prefer to have a seperate "home "partition", however, as you have FAT32 partitions that are readable from both Linux and Windows, I wouldn't bother.

---

### Post by richbarna on 2006-07-13
> **Radioactive Fellow said:**
> You can do the [COLOR=DarkSlateBlue]upgrade[/COLOR], your not going to lose any information stored.

 			 				5 GB FAT32 /dos

wtf! ;)

It actually says .5 = 512Mb. And yeah, I nearly missed it too ;)

---

### Post by Radioactive Fellow on 2006-07-13
> It actually says .5 = 512Mb. And yeah, I nearly missed it too 

Hahahaha, my bad, sorry

---

