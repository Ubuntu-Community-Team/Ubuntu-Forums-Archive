---
title: "Dual boot- XP and Ubuntu"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by OlyPerson on 2007-11-28
Ok, so I have Ubuntu on my old laptop and I like it and want to put it onto my desktop, dual booting XP and Ubuntu.  My main question is, is this safe?  I have only one hard drive, and my parents will be pretty angry with me if I mess up the computer (AKA I'll have to buy the computer).
So how do I go about doing this safely?  I have 50% of my hard drive open (of 80gb), but there isn't a very big space in it as I see when I defrag it.  Not sure if that's relevant though.  Could someone help me with a step by step process?
Thanks in advance.

---

### Post by siciliancasanova on 2007-11-28
I just gave this same link to someone else : [http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

Backup all your data, if you can.  To dual boot you will have to manually partition the HDD when you are installing Ubuntu or use gParted.  If you have never partitioned before, make sure you don't reformat the NTFS(windows) partition.

---

### Post by OlyPerson on 2007-11-28
How does one backup files without an external hard drive?

What are the chances that I do mess up my XP files?

And how do I make sure that I don't reformat the NTFS files?

---

### Post by schauerlich on 2007-11-28
1. CDs, DVDs, flash drives.
2. As long as you don't touch the XP partition, you should be fine, but it's still a good idea to back up your files. It might be 99% likely you won't lose any data without backing up, but it's 100% likely you won't if you do.
3. When you're on your partition table, don't touch anything formatted as ntfs.

---

### Post by siciliancasanova on 2007-11-28
Grab some dvds, burn important things like documents, photos.  Things that would be irreplacable.  I would forget about music or other things you downloaded that you could just download again if something were to happen.

The chances are slim that anything wrong will happen.  I would download and use gParted to create your partitions before you install ubuntu.

If you follow that guide it will give you an idea for partitions.  When I had dual boot I had

100gb for my Windows (NTFS)
20gb for my EXT3 / partition
60gb for my EXT3 / home partition
and 2gb for my SWAP partition

That's just me of course you need to set it up what's best for you.

When you get into gParted it's just going to list it as one big thing all as "NTFS" and you will select that you want to resize it into another partition of say "15gb" and it will ask you waht type and you can select "Ext 3"

Where you want to make sure you don't hit reformat is when you then put in the Ubuntu disk and you select to manually partition you will see all the partions you already created.  Just don't hit reformat on any of them.  Select your mount point for Ubuntu and if you have a /home partition select the partition you want for /home

I'm really tired of typing at this moment but if you follow that guide I posted it will explain all the options for partitioning.

---

### Post by oeolycus on 2007-11-28
Depending on OP's confidence with computer-futzing, it might just be easier to have the Ubuntu installer shrink the partition itself. Obviously, it's not as "custom-tailored" but there's less room for human error.

I second Siciliancasanova's sentiment though. **_Backup first!_**

It might not be worth trying at all if you're really worried about your parents. I've done some stupid things that took me hours to fix (fortunately, without data loss)--it's helped me become a lot more adept at working with Linux--but at the same time, it would have been nigh impossible to concentrate with anyone yelling at me! :)

---

