---
title: "Install Problems"
date: 2007-04-27
forum: Apple PPC Users
---

### Post by gwoodard on 2007-04-27
I am installing Ubuntu 6.10 on a Mac (Blue and White) G3 after I partition the Hard Drive, I get an overlapping partition error, and I cannot complete the install what should I do

---

### Post by dannyboy79 on 2007-04-27
what are you using to partition the drive with a head of time? if I were you, I would leave the space unallocate and let hte installer partition and format it's own space. so boot into the live cd, make sure you know what partitions are what, are you dual booting??? it would be smart to completely wipe all data from the failed install partitions. the BEST way to accomplish this is write zero's to them. then use the live cd to delete them and just leave the space unallocated. The reason you want to write zero's to the drive is because this way there won't be anything left in it's place. deleting a partition and reformatting an area can still leave behind stuff which with very expensive tools and software, SOME data can be recovered. you can use dd to wipe the partitions using this command. well first make sure they are mounted somewhere (i think it needs to be mounted first?) within your livecd. (IMPORTANT, if you're dual booting, make sure you know exactly which partitions your wiping/writing zero's to. Also, if you're dual booting and you're writing zero's to the drive I would make  sure you have a backup of your dual boot system before wiping anything)

sudo dd if=/dev/zero of=/dev/hda2 bs=2048k

Then delete the partition and make sure fdisk -l doesn't show it there since we deleted it. Then restart your computer  with  the live cd and perform the install and when partitioning comes up, chose manual partitioning it's not hard at all. Also, grub WILL get installed on your MBR which can overwrite other boot loaders and what not so if you need to save your mbr, back it up first with this command 

sudo dd if=/dev/hda of=/media/USBSTICK/MBR.img bs=446 count=1
adn this will back up the mbr of the first hard drive to an external usb stick mounted at /media/USBSTICK and it'll be named MBR.img, to restore it you would use this from a live cd.

sudo dd if=/media/USBSTICK/MBR.img of=/dev/hda bs=446 count=1

this won't overwrite your partition table which is in the space between 446 and 512. all this great info can be found here: [http://users.bigpond.net.au/hermanzone/p15.htm#How_to_back_up_and_restore_your_MBR](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_back_up_and_restore_your_MBR)
Herman is the MAN!!

IF you don't want grub installed on your MBR, than you need to download the Alternate Install CD which gives you way more flexibility. good luck

---

