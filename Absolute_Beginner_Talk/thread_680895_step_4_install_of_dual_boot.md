---
title: "step 4 install of dual boot"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by yuffie8 on 2008-01-28
ok so im at stage 4 where i specify how much gig to partiton to ubuntu, usually when i have installed ubuntu it comes with a lovely slider and it pretty much does it for you, however this time alas - it does not!

i have

 0 Guided - use entire disk
     0 SCSI1 (0,0,0)(sda) - 80 GB
     0 SCSI1 (0,1,0)(sdb) - 41.1 GB
 0 Guided - use the largest continuous space
 0 Manual


Ok so i desire to keep xp on the first disk and allocate about 60GB for ubuntu on there also, ill assume i should click 'manual'

so i have and this menu comes up ... any help allocating would be greatly appreciated!

---

### Post by PurposeOfReason on 2008-01-28
Are you trying to install in on /dev/sdb? If so, choose largest amount of free space.

---

### Post by yuffie8 on 2008-01-28
no im trying to install on sda, i installed it on sdb before and grub wasnt able to find windows, i was informed it might be sensible to install xp on sda again and then install linux also on sda (as i want a significant FAT32 partition - probably the entire sdb so i can just dump files in there)

---

### Post by PurposeOfReason on 2008-01-28
Then you're going to have to shrink /dev/sda1 by around 30000MB. Then make an Ubuntu partition in the new space (ext3, dev/sda2, mount point is /) with a size of 28000MB. Then a swap of everything that is left. You can choose your own sizes if those don't work for you.

---

### Post by bumanie on 2008-01-28
Personally, I always choose manual so I can be sure that /root, /swap and /home are set up as I want them to be. You can choose largest continuous space if you like, but you have less control over the outcome. If the outcome is not what you want, you can use the in-built partition editor or gparted live cd to change things to how you want it, however

---

### Post by yuffie8 on 2008-01-28
ok ok sounds cool, when i click 'edit partition' on the 80015MB it lets me change the 
use as : ntfs
mount point : /media/sda1

but no resize section, i dont want to delete the partition, should i 'delete partition' and then make a new one ? Surely doing this will delete my xp partition ?

---

### Post by PurposeOfReason on 2008-01-28
> **yuffie8 said:**
> ok ok sounds cool, when i click 'edit partition' on the 80015MB it lets me change the 
use as : ntfs
mount point : /media/sda1

but no resize section, i dont want to delete the partition, should i 'delete partition' and then make a new one ? Surely doing this will delete my xp partition ?
Do not do that, you will lose your data. Are you under the manual partition? If so, I have no idea why it wouldn't work.

---

### Post by yuffie8 on 2008-01-28
yeah i am in the manual partitioner, the screen infront of me is like the picture with the opening post.

no worries, thanks anyway

---

### Post by bumanie on 2008-01-28
To do what you are proposing, it would be much safer for you to download and burn a gparted live cd. It has been designed specifically for partitioning and is easy to use due to having a gui. Also, before changing any partitions, it is always a good idea to defrag windows first. I really think gparted will be your best tool for what you want to do, you will greatly reduce your chances of damaging your windows install this way.

---

### Post by yuffie8 on 2008-01-28
ok cool, ill do that then. I just installed windows like 2 hours ago - should it still need defraging ? Ill boot into windows and do it anyway. Cheers, i have no idea why the slider thing isnt there though.

---

### Post by bumanie on 2008-01-28
> ok cool, ill do that then. I just installed windows like 2 hours ago - should it still need defraging ? Ill boot into windows and do it anyway. Cheers, i have no idea why the slider thing isnt there though.
If you only installed 2 hours ago, it won't need a defrag. 
After I looked at your sreenshot agian, I realised with the manual method, and you wanting to put ubuntu on c:\ partition, you first need to partition with something else or the ubutnu partitioner was going to wipe everything.

---

### Post by b0b138 on 2008-01-28
I have just setup a duel boot and had problems with the same step your on.  Since you said you just installed windows a couple hours ago, Im assuming you wont miss anything if you do it again.  Except this time, on the xp install, dont partition the whole drive. Partition out however much you want for xp and leave the rest alone. Then when you get to the ubuntu install, you can tell to use largest contiguous free space.

There is also a resize partition utility under system/administration? but I kept getting errors trying to resize my ntfs partition.

---

### Post by ADH on 2008-01-28
I am a not overly computer literate person, but I got great help setting up my multi-boot system (I have two IDE hard drives.)  My primary OS is eComStation 1.2R (OEM version of IBM's OS/2 Warp 4.52) on the master drive, so I use IBM's Boot Manager to control my booting.  I have a 10 gig Windows XP partition on the master, which is usually booted to solely to update the antivirus, antispyware, and Adaware data files.

Last year, I decided I at wanted to try Linux, so I got a lot of advice and assistance about adding it to my system.  I wanted Ubuntu on my second drive, and didn't want Grub messing up my master drive and system (that happened once, when I didn't select Custom install - fortunately, I had backed up eCS and XP just before the Ubuntu install attempt), selected Custom install, created 3.5 gig root partition, 3.5  gig home partition, and a SWAP partition using a shareware drive utility, and directed Grub to the slave drive.  All worked fine - if I select Ubuntu from the Boot Manager menu, Grub appears, then Ubuntu boots.  I'm using Ubuntu Firefox at the moment - I haven't learned much else yet.

---

### Post by yuffie8 on 2008-01-28
Im going to give gparted a go, if i cant get it to work ill install xp again and give it only a smaller partition, thanks for the idea, as i say tho ill try gparted first

---

### Post by ajgreeny on 2008-01-28
Gparted is already on the ubuntu live CD so no need to download anything else.  Run ubuntu liveCD, go to gnome partition editor and when it comes to its gui simply shrink the windows partition, sda1, to whatever size you want.  Now in the unallocated space left, make an ext3 partition for ubuntu with mount point / (root), but leave a GB or something like to make a swap partition for ubuntu.  sdb can then be formatted as fat32 or even ntfs now as a shared drive between windows and ubuntu.

I hope this makes sense to you.  If you've already done the job successfully just ignore this, but if not it may just clarify things a little.  Good luck!

---

