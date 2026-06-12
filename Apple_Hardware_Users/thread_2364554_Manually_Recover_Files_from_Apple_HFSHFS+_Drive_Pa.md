---
title: "Manually Recover Files from Apple HFS/HFS+ Drive Partition"
date: 2017-06-24
forum: Apple Hardware Users
---

### Post by ducdeguermantes on 2017-06-24
I recently installed Ubuntu 16.04 on a partition of my Macbook Pro (c. 2016) hard drive and corrupted the boot loader for OSX. I don't use Terminal much, so I am not familiar with all of the commands. 

I can boot cleanly in Ubuntu, but can't manage to get a backup of the files on my Apple HFS/HFS+ hard drive partition made through Ubuntu Terminal – I've also tried doing this by booting my laptop in Target Disk Mode, connecting it to another Macbook via Thunderbolt 2.0, and using Terminal there. 

On the other Mac, I tried dd, cp -av, asr restore, and rsync -av to try to move the files over to an external hard drive with /dev/diskN as my target. For dd I got a permission denied response. For cp it told me that /dev/diskN is not a directory. For asr it told me that file copy is not supported anymore. For rsync it told me that /dev/diskN is not a directory.

In Ubuntu, I've tried sudo -s dd if=/dev/sdaX of=/dev/sdcX which initiates alright, but ends up only copying over 650MB of a 650GB partition.

I've also tried using TestDisk, but haven't figured out how to use it to repair a partition table. It found one error, but didn't give me a clear way to repair it after doing a quick scan of my full 1TB drive.

Please accept my apologies if I am posting this in the wrong place or not describing these issues correctly. My assumption is that there is some combination of a broken partition table and a security or permissions issue with the HFS partition of the drive (though I definitely did not have FileVault turned on). Any help would be greatly appreciated.

---

### Post by howefield on 2017-06-24
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by ducdeguermantes on 2017-06-25
Problem solved. Not sure how to delete this thread.

---

### Post by oldos2er on 2017-06-25
To mark it solved use Thread Tools at the top of the page.

---

