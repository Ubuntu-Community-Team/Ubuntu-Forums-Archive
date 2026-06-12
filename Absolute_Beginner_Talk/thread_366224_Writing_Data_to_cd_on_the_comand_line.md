---
title: "Writing Data to cd on the comand line"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Micronot on 2007-02-20
I'm new to linux so please forgive such basic questions. I'm running Dapper Drake. I have a crashed gnome setup. I have since reinstalled on a seperate partition. The original partition can only be accessed in recovery mode. I want to save my original my original & most loved  files to cdrom. I'm a novice on the comand line especially. This is what I've tried-

I tried to use cp to copy entire directories but it won't let me do it. OK fine.
So, I've Chosen the most important individual files & copied them using the cp command to /media/cdrom0.

Everytime I use the ls /media/cdrom0 it displays all the files ive copied. But when I put the cd back in the computer while running the new partition, it shows as an empty cd. what am I missing.

---

### Post by chggr on 2007-02-20
> **Micronot said:**
> I'm new to linux so please forgive such basic questions. I'm running Dapper Drake. I have a crashed gnome setup. I have since reinstalled on a seperate partition. The original partition can only be accessed in recovery mode. I want to save my original my original & most loved  files to cdrom. I'm a novice on the comand line especially. This is what I've tried-

I tried to use cp to copy entire directories but it won't let me do it. OK fine.
So, I've Chosen the most important individual files & copied them using the cp command to /media/cdrom0.

Everytime I use the ls /media/cdrom0 it displays all the files ive copied. But when I put the cd back in the computer while running the new partition, it shows as an empty cd. what am I missing.

The fact is that you dont need to get into all that trouble (writing CDs). I understand that you have two separate partitions with Ubuntu installed on them, but the one does not work. You simply want to copy files from the broken partition to the new one. Is all this information right?

If it is, the only thing you should do is boot into the good partiotion and use the command line to mount the broken partition. Then you can transfer your files safely and quickly. Follow these steps (I assume that the broken partition's device under linux is /dev/hda1 and that its filesystem is ext3. Change these parameters according to your needs):

1) Boot the computer into the Ubuntu partition that works OK
2) Open a terminal and write
sudo mkdir /media/Broken
sudo mount -t ext3 -o rw /dev/hda1 /media/Broken
3) Your previous corrupted filesystem is located inside the folder /media/Broken and you can copy all the files you want.

---

### Post by Micronot on 2007-02-21
Thanks- That worked perfectly!

---

