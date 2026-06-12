---
title: "Partition advice with multi boot on Laptop"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by hairywombat on 2007-05-09
All,

I searched high and low but didn't really find a clear solution to help in my migration...

I'm running a toshiba laptop with primary partitions:
[XP][Feisty][swap][recovery]

The recovery is a 3GB FAT32 XP install image so that one can boot to and reinstall XP clean if all goes wrong. It's comes from Toshiba like that.

My problem is that I want to create another partition (probably FAT32) that is shared by XP and Ubuntu for common stuff like music,photo's, general data. Of course I'm at the limit of 4 primaries so I guess my options are to delete one (would have to be the recovery) or preferably convert one to an extended to allow logicals under it. Is this possible/sensible?

I would appreciate some advice as to the most simple and low risk scenario. By the way, I have been using the GParted live CD so far which is excellent.

TIA,
wombat

---

### Post by Thingymebob on 2007-05-09
I Have a similar setup, my swap and home partitions are both inside an extended partition as well as my slackware root.

Just remember to update /etc/fstab to reflect your new layout (you should be able to do this from within the gparted livecd after mounting your feisty partition) 

I don't have a windows partition but believe that needs to stay on the first primary.

---

### Post by starcraft.man on 2007-05-09
> **hairywombat said:**
> All,

I searched high and low but didn't really find a clear solution to help in my migration...

I'm running a toshiba laptop with primary partitions:
[XP][Feisty][swap][recovery]

The recovery is a 3GB FAT32 XP install image so that one can boot to and reinstall XP clean if all goes wrong. It's comes from Toshiba like that.

My problem is that I want to create another partition (probably FAT32) that is shared by XP and Ubuntu for common stuff like music,photo's, general data. Of course I'm at the limit of 4 primaries so I guess my options are to delete one (would have to be the recovery) or preferably convert one to an extended to allow logicals under it. Is this possible/sensible?

I would appreciate some advice as to the most simple and low risk scenario. By the way, I have been using the GParted live CD so far which is excellent.

TIA,
wombat

Far as I know, swap doesn't have to be primary...... its just swap space after all. 

Just a word of advise, I used to have one of those partitions on my drive... I got annoyed though cuz for some reason it stopped booting into the reinstall menu. The only real reason for companys putting this on your drive instead of a CD is to screw you so you have to reinstall their crap every time you go back to preinstalled. So, my easy solution was to enforce my own fair play use, I paid top dollar for my PC and I think that means I should have a CD, so I went on bit torrent and got a copy of XP SP2, Your key should work, long as your same version (i.e. home for home CD, pro for pro CD). Hope pointing you to bit torrent doesn't violate any piracy rules, I think its fair use anyway :)

So ya, I'd make swap logical and delete your recovery partition. Then you got 1 primary and 2 extended slots left (did I get my math right, gah, I never remember the right max numbers...) :)

---

### Post by apunc1 on 2007-05-09
I dont think you need to delete anything. you can resize one of the partitions and from the newly freed space create the ext3 partition. more info here [http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

I think if one of the four primary partitions is an extended partition, it can be subdivided into logical partitions
more on partitioning here [http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

sorry i have never done what you wish to accomplish before but I think you can find a solution to your problem through the links above.

---

### Post by hyper_ch on 2007-05-09
Only the windows partition needs to be primary... the linux root one hasn't to be primary either :)

---

### Post by Inxsible on 2007-05-09
I got rid of my recovery partition once i created recovery discs AND copied the partition onto my external hdd.
 
If you have enough space, you can make the Feisty as an extended partition and then create 3 partitions within it
/ for root
/home for home
/data - which will be a shared drive between XP and Feisty. 
 
 
But you will probably have to keep it in EXT3 and not FAT32 since / and /home have to be EXT3 for installing Feisty and you cannot have more than 1 filesystem in the same extended partition.
 
You can then use [http://fs-driver.org/](http://fs-driver.org/) to access that partition from XP.
 
Or you could put the swap in the extended partition and have a new partition(FAT32 if you like) where you currently have your swap

---

### Post by hairywombat on 2007-05-09
Thanks for the advice so far. Now that I know Feisty and Swap can be on logicals then my strategy would be to convert them to an extended like so:

[XP][EXT(feisty)(swap)][Data][recovery]

The question is, is it possible to 'convert' primary partitions to logicals on and extended partition without losing the data? Any tips.

I assume I would also have to reconfigure Grub and also tell Ubuntu where swap has gone (with fstab I presume)???

Cheers.

---

### Post by hyper_ch on 2007-05-09
there is no way that I know that you can convert without loosing the data.... what data do you have in Feisty already that is important?

If it's not too much you could do the following:

(1) Install the Ext2/3 Drivers for Windows
(2) Copy all the important data from the Feisty partition to the windows one
(3) Delete the feisty and swap partitions
(4) Make a logical one
(5) Re-create the Feisty and Swap partition
(6) Reisntall feisty
(7) Put the stuff back from Windows :)

---

### Post by Thingymebob on 2007-05-09
> **Inxsible said:**
> But you will probably have to keep it in EXT3 and not FAT32 since / and /home have to be EXT3 for installing Feisty and you cannot have more than 1 filesystem in the same extended partition.
Am i reading this right? I have swap, reiserfs and ext3 in my extended partition and it all works just fine

---

