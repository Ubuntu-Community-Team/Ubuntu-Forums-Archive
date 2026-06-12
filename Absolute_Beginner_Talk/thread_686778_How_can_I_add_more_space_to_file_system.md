---
title: "How can I add more space to file system?"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Reggie Manzer on 2008-02-03
I recently Installed Ubuntu and loved it so much I asked myself "why was am I still keeping windows XP around when all it does is hog space?" So I deleted It off my computer. The problem is, that when I originally partioned my hard drive, it split it into three parts, and now my computer uses the other partions as external disks that have to be loaded everytime I turn on my computer. I also have reached the maximum space used in file system, so is there any way to add the space that used to be occupied by windows to file system?
Thanks.
-Reggie

---

### Post by candtalan on 2008-02-03
In theory you can change some partition sizes. In practice there is a considerable risk of loosing all data if things go wrong because of - say - lack of experience, so beware.

Have a good backup of data anyway, on an external device, that is one which is not affected by the target disks partition table.

Maybe then use one of the partitions to act as a convenient data store, copy data into it, then edit the other partitions, delete one or two, maybe resize one,  to your satisfaction. If you end up resizing - enlarging - your ubuntu system partition, then it will be what you wish for. However, if the swap partition is renamed then you will get significant trouble (for a beginner) to sort out. In fact any renaming which will happen automatically after deleting - is likely to cause complications for you. Also note that it is quite possible if not likely, that you have an 'extended' partition function on the disk, and this will restrict your options.

If all you do is to resize partitions (only) no deletions, then it will I think, work more easily. 

Ultimately, your 'worst' case (it would be my first choice though) would be to reinstall over the whole disk, (losing its data) and then copy back the data originally saved.

Note also that alien partitions can easily be used and automatically mounted at log in, by use of simple edit in the fstab file, though this does not answer all your stated needs just now.

hth

---

### Post by ugm6hr on 2008-02-03
Maybe make the former XP partition into an Ubuntu /home partition?

Lower risk of data loss that way.  And you get the benefit of a separate /home partition (for future upgrades etc).

[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by philinux on 2008-02-03
> **Reggie Manzer said:**
> I recently Installed Ubuntu and loved it so much I asked myself "why was am I still keeping windows XP around when all it does is hog space?" So I deleted It off my computer. The problem is, that when I originally partioned my hard drive, it split it into three parts, and now my computer uses the other partions as external disks that have to be loaded everytime I turn on my computer. I also have reached the maximum space used in file system, so is there any way to add the space that used to be occupied by windows to file system?
Thanks.
-Reggie

I assume you were dual booting. If so you could use gparted to resize youe exixting partitions. The file system need to be unmounted so this is best done from the gparted live cd or the ubuntu livecd. Besure to backup any data first. Also moving home to its own partition has advantages. Click the psychocats link and one of the links has instructions for this.

---

### Post by hyperair on 2008-02-03
I've done some major filesystem resizing before and it went through flawlessly. I did it without backing up, though what I did was highly unadvisable and I only did that because I didn't have an external storage to back up onto.

---

### Post by bumanie on 2008-02-03
Gparted live cd is definitely the best tool for you to use. I have resized, deleted, copied and shifted partitions without ever losing any data. I would however back up anything that is important, because things can go wrong ie a power outage partway through. As philinux says a separate /home is a good idea, because in theory, if something happened to go wrong with ubutnu, you should only need to reinstall the file system to / and your data should be safe.

---

### Post by Reggie Manzer on 2008-02-05
Thanks Everyone, I was able to successfully resize my filesystem and now I can better enjoy ubuntu without the worry of running out of space! Thanks. Reggie

---

### Post by hyperair on 2008-02-05
@Reggie Manzer: Perhaps you should mark the thread as solved, since it seems to be?

---

### Post by jesusfreak107 on 2008-02-05
yes, mark it as solved, or people like me will still continue to leak in, looking for people to help.  It is hard to help people when you cannnot find anyone looking for help because there are so many misleading threads.

---

