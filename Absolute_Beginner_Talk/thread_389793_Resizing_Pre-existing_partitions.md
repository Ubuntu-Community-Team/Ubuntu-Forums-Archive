---
title: "Resizing Pre-existing partitions"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Staplerchild on 2007-03-21
Hey guys. I currently have a Ubuntu Windows dual boot running on my laptop, and each of these partitions takes up around 53 GB of space. I am thinking of resizing each partition to around 15 GB and creating a new fat32 partition for all my files, because I want them to all be in the same place.

I was wondering if this is safe. The (second) last time I used gparted I completely destroyed my computer, but my friends attribute this to my being stupid, though I ended up installing the dual boot successfully (eventually... as in, on the third go XD). I have never resized an ntfs partition before though, so I don't know how it will react.  

I have been reassured by a few people, but I really want to make sure nothing will happen. I don't have very many really important files, but I don't want to have to reinstall Windows.

Thanks! :)

---

### Post by KenSentMe on 2007-03-21
Well, resizing is not 100% safe, so i would advise you to always make a backup of your files, in case something goes wrong.

For the resizing of partitions i would use the gparted livecd ([http://gparted.sourceforge.net/livecd.php)](http://gparted.sourceforge.net/livecd.php)), because you can't resize a partition with a tool that is running on that partition.

But be sure to make backups.

---

### Post by Circus-Killer on 2007-03-21
personally, im totally against resizing partitions. i always go for the clean install approach.

if you plan to resize your partition, backup your data, and be prepared to do a clean install afterwards. :???:

---

### Post by Bachstelze on 2007-03-21
Agreed with KenSentMe. GParted Live CD, backups of valuable data just in case and you will be fine.

---

### Post by indytim on 2007-03-21
Just as a point of reference... a couple of months ago I also embarked on a significant "re-sizing" effort via GParted Live.  All went well until I resized my Windows (NTFS) partition (which was my boot partition also).  The net result in my case was a partition table that got totally messed up.  Ended up doing a clean wipe of the h/d and rebuilding from scratch.

If you're going to do ext3 partition re-sizing via GParted (my experience level), my suggestion would be to re-size one partition at a time.  Don't stack up multiple partition re-sizings in one job.

IndyTim

---

### Post by belikralj on 2007-03-21
I never tried to resize NTFS from Ubuntu but isn't it true that Ubuntu isn't that reliable with writing to NTFS, and if so how reliable is it resizing NTFS? Personally I would my self use Partition Magic for the Windows partition, but I would like to warn that I did have problems when Partition Magic rebooting the computer and messed up my grub so I ended up having no option other than to reinstall. I solved this by getting two separate discs for Ubuntu and Windows. If you have separate discs it shouldn't be a problem, but if not don't try it. And as the guys said for resizing ext3 gparted is the best. Again I'm not so sure my self so if some one could clear it up for me whether gparted is ok with resizing NTFS

---

### Post by Bachstelze on 2007-03-21
I personnally never had any problem resizing NTFS with GParted, either in it's own Live CD or Ubuntu's, but I had countless of them with PartitionMagic...

---

### Post by Staplerchild on 2007-03-21
Is the Gparted LiveCD any better than the gparted that comes with the Ubuntu LiveCD?

---

### Post by Bachstelze on 2007-03-21
It has a more recent version of GParted so it has better support for some filesystems. Also, the GUI is more minimalistic so it is light and fast, while Ubuntu's live CD requires a fairly stongmachine and takes forever to load.

So yes, if you ask me, it's a million times better ! But of course, no websurfing or email while it is partitioning, which can take a while.

---

### Post by Staplerchild on 2007-03-21
Alright, I'm going to give this a try when I get home tonight.
Wish me luck. XD

---

### Post by indytim on 2007-03-21
You might have been able to save youself a bit of effort by using the Super Grub Live CD to restore your boot GRUB rather than a complete re-build.  SuperGrub can be found here : [SuperGrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

IndyTim

---

### Post by Staplerchild on 2007-03-21
Okay, so, I resized the partitions and windows and ubuntu both responded fine. However, after I turned the unallocated spaces into fat32 spaces, I got some issues. This might be because I was dumb and extended the ext3 space with my swap in it so I could have two fat32 partitions, but now I can't seem to boot into ubuntu anymore.

Basically what happens now is the ubuntu boot screen show up and, right after that it goes "activating swap, checking filesystems, checking filsystems" and then nothing happens.

What exactly have I done? :s
Can I fix this?

---

### Post by Staplerchild on 2007-03-22
Anyone? ;_;

P.S.: I can still log into ubuntu recovery mode...

---

### Post by Bachstelze on 2007-03-22
Make sure your fstab still has the correct partition numbers. Maybe they chabged and it still looks for the old one. Also, what do you mead "ext3 with my swap in it" ? You created a swap file ?

---

### Post by Staplerchild on 2007-03-22
No, the swap was created during the ubuntu install, and it was created within an ext3 partition.

Anyway, could you clarify what you mean? I'm a real beginner, so I need... help. :(

---

### Post by Staplerchild on 2007-03-22
Would I have to edit fstab using the livecd again?

---

### Post by Staplerchild on 2007-03-22
*Bump*

---

### Post by Staplerchild on 2007-03-22
Wouldn't I get an error specifying if the problem was in fstab? Or my system wouldn't boot at all, right?

---

### Post by Bachstelze on 2007-03-22
Please pop in a live CD and paste the output of *sudo fdisk -l*.

---

### Post by Staplerchild on 2007-03-22
Argh sorry, I was just about to leave from work when I saw your reply, and it takes me about two and a half hours to get home.

Anywyay, here it is:
Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1977    15880221   83  Linux
/dev/sda2   *        6913        8889    15880252+   7  HPFS/NTFS
/dev/sda3            8890       14410    44347432+   5  Extended
/dev/sda4            1978        6912    39640387+   b  W95 FAT32
/dev/sda5           13824       14410     4715046   82  Linux swap / Solaris
/dev/sda6            8890       13823    39632292    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 129 MB, 129499136 bytes
33 heads, 32 sectors/track, 239 cylinders
Units = cylinders of 1056 * 512 = 540672 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         240      126448    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 32, 32) logical=(239, 16, 32)


:S

---

### Post by Staplerchild on 2007-03-22
Oh also, earlier, I meant to say a swap file in an extended partition, not an ext3 partition. :(

---

### Post by Staplerchild on 2007-03-22
I tried fscking everything to check for inconsistencies but nothing is wrong that I can see. =x

---

### Post by Staplerchild on 2007-03-23
Kernel panic. :S

Guess I'm going to have to go for the full reinstall now. :S

---

