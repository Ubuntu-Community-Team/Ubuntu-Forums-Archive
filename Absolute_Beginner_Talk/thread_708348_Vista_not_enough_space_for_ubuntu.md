---
title: "Vista not enough space for ubuntu"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by gitwick on 2008-02-26
Hi,
I have a laptop with 80 gb hard disk space with two partitions of 70 and 10 gb.
I wanted to dual boot my pre installed vista with ubuntu as per instructions i tried to shrink my vista but the max free space it created (i shrunk both c and d drives) was 5 gb
i am confused i wanted atleast 20gb for my linux
though i have 36gb freespace on my laptop as of now

please help

---

### Post by OldGrey on 2008-02-26
Bit confused by your post. You say that you only have 5Gb of hard disk space and then later 36Gb. Which is the case. If the latter you should be able to install Ununtu into the 36Gb of freespace no problem.

---

### Post by imT on 2008-02-26
**a very subjective opinion** : vista is a sad choice and i don't wanna treat this matter now, if you are tied with windows use xp pro sp2 (better if is modified to be corporate) but the very best would be a unix based system, linux most probably, ubuntu more exactly cus of the precious community :) so my choice would be to backup all the data and then a clean install with ubuntu, "/home" partition being mounted on a diferent partition...

---

### Post by shad0w_walker on 2008-02-26
You will need to defrag your windows drive as much as possible before shrinking, otherwise good old NTFS (Mostly old) will leave files all over the place and use up tiny parts further into the disk and stop you shrinking the partition.

---

### Post by gitwick on 2008-02-26
i completely agree but i got vista preinstalled i wanna remove it compleletly how do i do it im scared i love my new laptop

---

### Post by piousp on 2008-02-26
Backup ALL your data. I also have a laptop with vista pre-installed. . . first thing i did: installed kubuntu.
Dont be afraid of erasing windows. . . instead, be happy that you can erase it!

---

### Post by OldGrey on 2008-02-26
Have you tied running ubuntu as a live cd? If everything works then you can install by clicking on the install icon and accepting the option to wipe the hard drive and install Ubuntu. However if you do Vista has gone forever unless you have a Vista installation disc. 

Alternatively the installation caters for dual boot, which IMHO, is not to be dismissed as an option until you are sure you are happy with Ubuntu.

---

### Post by lswest on 2008-02-26
yeah, i had the same problem, something about estimated size required for shadow backups and system restore points.  After i disabled those and defragmented my drive, i was able to shrink it more than before.  Give it a try.  Also, try cleaning up the shadow backups and restore points (right-click your drive, properties, clean up), in case you want to keep Vista around for a bit.

---

### Post by sayakb on 2008-02-26
To free up more space, open command prompt and type
powercfg -h OFF
This would disable hibernation and free up as much space as your RAM's size.

Also, turn off system restore as indicated.

---

### Post by az on 2008-02-26
> **lswest said:**
> yeah, i had the same problem, something about estimated size required for shadow backups and system restore points.  After i disabled those and defragmented my drive, i was able to shrink it more than before.  Give it a try.  Also, try cleaning up the shadow backups and restore points (right-click your drive, properties, clean up), in case you want to keep Vista around for a bit.

I recently installed on a vista system and get the same thing.  Instead of doing what you suggest, I just popped in the Ubuntu live cd and used the linux partitioner to create more space.  Vista home basic will work fine on a partition of 20GB or more.  All the other version need 30GB, I think.

My point is that you get a lot more flexibility when you use the linux partitioning tools.

If you don't want to install linux, you may need to reinstall the Vista bootloader after shrinking the partition.  You don't need to do that step if you are installing Ubuntu as well, since the Ubuntu bootloader (grub) will take care of booting both OSes.

---

### Post by lswest on 2008-02-26
a word of warning about using gparted on resizing vista, defrag it first, and disable your virtual memory before you do, else there is a very good chance (as happened to me) to mess something up.  Actually, if you can, it's best to use the vista partitioner to resize vista.

---

### Post by az on 2008-02-26
> **lswest said:**
> a word of warning about using gparted on resizing vista, defrag it first, and disable your virtual memory before you do, else there is a very good chance (as happened to me) to mess something up.  Actually, if you can, it's best to use the vista partitioner to resize vista.

The virtual memory is on the partition as a file.  The linux partitioning tools will not break it.

The older version of the partitioner had issues with Vista-created NTFS volumes, but this has been fixed for a while now.

---

### Post by lswest on 2008-02-26
okay, thanks for clearing that up, and i didn't mean the file would be broken, just it has happened to me once or twice that vista allocates that space as "free" but still won't let you partition it away, which is logical i guess, but nonetheless a nuisance.  (that remark was meant for if you're trying to resize within Vista)

---

