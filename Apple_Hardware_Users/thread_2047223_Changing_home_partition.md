---
title: "Changing /home partition"
date: 2012-08-24
forum: Apple Hardware Users
---

### Post by Kopkins on 2012-08-24
I started using Ubuntu on my macbook back at the beginning of this year and though 50Gb would be plenty of room for everything. I'm getting close to the point where I'm running low ~75% space used. I have a huge chunk of space available on the disk, but there are other partitions in the way. Take a look at my partitions and let me know what the best option is. I would like to combine my current /home partition with that huge free space, but I'm not sure if that is an option. 

The other option is to just use the big free partition as my /home. 
Could I just do ```
dd if=/dev/home/partition of=/dev/new/partition
```
Then change my /home partition in fstab?

Thanks,
Kopkins

---

### Post by oldfred on 2012-08-24
Moved to Apple sub-forum.

I do not know Macs but with gpt do not use any dd type programs. With Windows in a Mac you have to have the hybrid MBR/gpt configuration. The Mac is an older UEFI system and Window is still in BIOS with MBR. Paritions for the Mac are gpt  but Windows only boots from gpt with a newer UEFI or BIOS/MBR.

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
[http://www.microsoft.com/whdc/device/storage/GPT_FAQ.mspx](http://www.microsoft.com/whdc/device/storage/GPT_FAQ.mspx)

The author of gdisk posted once here not to use dd as gpt partitions have internal structures that cannot be bit by bit copied without creating issues.

Someone with a Mac should really comment, but I would think you can copy with rsync.

To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Kopkins on 2012-08-24
Thank you. Very useful to know before I go ahead and try it only to make a mess of everything. Any apple users have any knowledge?

Kopkins

---

### Post by Kopkins on 2012-08-27
Following this, 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
I got as far as renaming /home to /old_home, but terminal says that device or resource is busy and it can't mv it. 

Not sure what to do.

Here's another shot of my partitions. 

Kopkins

---

### Post by oldfred on 2012-08-27
Did you change to / ?

cd / && sudo mv /home /old_home && cd / && sudo mkdir -p /home

---

### Post by Kopkins on 2012-08-27
Yes I did. Eventually I just changed fstab to not mount my old /home partition and instead to mount the new one. I've been using the new /home partition for an hour or so without problems now. I'm just going to reformat the partition I don't need anymore and leave it empty for now. I'm ending up with about the same result.

For reference if anyone else encounters this issue I'm attaching my original fstab and the modified (current) fstab, along with a snapshot of my current partition layout.

Solved,

Thank you oldfred

Kopkins

---

### Post by oldfred on 2012-08-27
Glad it worked. :)

---

