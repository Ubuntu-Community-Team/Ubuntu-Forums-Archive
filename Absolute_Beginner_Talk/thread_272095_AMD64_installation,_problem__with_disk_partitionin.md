---
title: "AMD64 installation, problem  with disk partitioning"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by kester111 on 2006-10-05
Am trying to install the 64 bit distro on my laptop
as dual boot with WinXP and have problems partitioning the disk...

The machine: HP pavilion dv6000 with the AMD Turion 64bit processor

The disk: 120 GB ATA Toshiba 

There are 3 partitions on the disk. sda1 is the main windows
partition with 101 GB and is ntfs. sda2 is a fat32 partition which I believe is the recovery partition. sda3 is a 1GB ntfs partition of whose contents and purpose I have no idea. There are a few MB of free space between sda1 and sda2.

On trying to install, I seem to have three options; erase the 
whole disk, which I don't want because I'd like to keep windows,
install in the largest continuous free space, which doesn't work because the largest free space is just a few meg, and manually partition, which is where I am. 

I try to resize the windows sda1 partition down to about 50GB,but this operation fails with an unknown error. 

I have encountered similar disk problems trying to install 
various SuSe and Redhat distributions. My next step will probably have to be partition magic. Failing that, I might 
try deleting the whole disk and reinstalling windows, perhaps
from the rescue disk. 

I could install linux on an external drive, but this rather defeats the purpose of a laptop. 

I'm not a linux expert and have little grasp of what I'm doing here. Any and all advice would be gratefully received. Also, 
if anyone has succeeded in installing on an HP pavilion 64 bit machine, that would be good to know.  

- Kester

---

### Post by gn2 on 2006-10-05
Have you tried posting here: [http://www.ubuntuforums.org/forumdisplay.php?f=134](http://www.ubuntuforums.org/forumdisplay.php?f=134)

64 bit can be problematic, I would suggest the 32 bit version to start off with.

Have you checked if there's 50gb free at the end of the drive?
A quick look at disc de-fragmenter will show you where all the data is.

It might need to be moved along a bit during the re-size.....
Doubt if Ubuntu installer will do this for you.
Easiest way I know of doing this is with Partition Magic, but I'm sure there's other disc partitioning utilities out there that are free...

---

### Post by Mr Pink57 on 2006-10-05
Usually the space needs to be raw, as if they are all partitioned it will just reconize the disk as a whole.  So if you can wipe a partiton to be nothing and let ubuntu format it.

pink

---

### Post by kester111 on 2006-10-06
Yeah, I think the problem is that the existing partitions
span the whole disk, right to the end. Next week I will maybe try to use partition magic to resize them.

Does anyone know, if I select 'erase entire disk' instead of partitioning it, should I be able to restore winxp 
with the recovery disks?

---

### Post by gn2 on 2006-10-06
If these are software recovery discs supplied with a brand-name PC, then they'll aalmost certainly wipe the disc clean, as they're designed to return the disc to it's original shipped state.

In order to re-install XP and configure install partition size you'll need an XP install disc. So long as you use your existing product activation key, a borrowed CD will do fine, if you know anyone that's got one.....

---

### Post by ReaderRat on 2006-10-06
I have found that it helps in resizing that you need to run Windoze disk defragmenter at least once (maybe several times) to get all your windoze files at the front of the disk,so you can resize the partition. Hope this helps.

---

### Post by gn2 on 2006-10-06
> **ReaderRat said:**
> I have found that it helps in resizing that you need to run Windoze disk defragmenter at least once (maybe several times) to get all your windoze files at the front of the disk,so you can resize the partition. Hope this helps.

Always a good idea to defrag first, but Partition Magic will move the data out of the way during a re-size.

I know it's paid for software, but it's worth the money if you do a lot of installs/partitioning in Windows.

---

### Post by majorvybz on 2006-10-24
I am planning to buy this laptop my self---tell me is this baby super-fast,,, and also did you get linux to work properly...also did the wireless system work....

I really like this laptop from the reviews i have been seeing,

---

