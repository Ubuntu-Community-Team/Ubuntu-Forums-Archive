---
title: "Partitions For Dual Booting XP &amp; Ubuntu"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Chaos45 on 2007-11-11
I plan on getting a new laptop soon and I've decided I want to dual boot Windows XP and Ubuntu. My question is about partitioning my hard drive for such an endeavor. I've never used Linux or created a partition before, and as such the prospect of creating a dual boot system with both XP and Linux is an especially daunting one. I've looked around and so far it seems that I would like to partition it in the following way:

Windows XP - NTFS
Ubuntu / - EXT3
Ubuntu /home - EXT3
Swap - 2GB
Shared data between XP and Ubuntu - NTFS

I will have an approximately 250GB hard drive, and 2GB of memory (I haven't actually bought it yet, so this might change a bit). I was wondering how much space I should be allocating for each of these, and how the shared data portion would work. 

Any information or input on the subject would be greatly appreciated. Thank you for your time. :)

---

### Post by Dr Small on 2007-11-11
> **Chaos45 said:**
> I plan on getting a new laptop soon and I've decided I want to dual boot Windows XP and Ubuntu. My question is about partitioning my hard drive for such an endeavor. I've never used Linux or created a partition before, and as such the prospect of creating a dual boot system with both XP and Linux is an especially daunting one. I've looked around and so far it seems that I would like to partition it in the following way:

Windows XP - NTFS
Ubuntu / - EXT3
Ubuntu /home - EXT3
Swap - 2GB
Shared data between XP and Ubuntu - NTFS

I will have an approximately 250GB hard drive, and 2GB of memory (I haven't actually bought it yet, so this might change a bit). I was wondering how much space I should be allocating for each of these, and how the shared data portion would work. 

Any information or input on the subject would be greatly appreciated. Thank you for your time. :)
Greetings,
Please take a look here for Dualbooting Ubuntu with XP:
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

Dr Small

---

### Post by Chaos45 on 2007-11-11
> **Dr Small said:**
> Greetings,
Please take a look here for Dualbooting Ubuntu with XP:
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

Dr Small

Thanks for the quick response :)

I have looked at this, but I was looking for more advice regarding in what way to set up my partitions. I realize there probably isn't a "best" way to do this, but I'm curious as to how well the aforementioned partitions would work (specifically the shared data portion) and how much space each would require on my hard drive.

---

### Post by rsambuca on 2007-11-11
As you say, the best partition scheme is dependent on the user and your individual needs.  As a good starting point, though, I would suggest something like 20GB for XP, 12GB for Ubuntu, 1GB swap (2 is probably overkill), and the rest a shared ext3 data drive.  On the shared drive, I would put my /home directory on it, as well as the XP "my Documents" folder, as well as shared media.  You can have XP read/write to the ext3 drive with the [FS-driver for windows]("http://www.fs-driver.org/").

---

### Post by Chaos45 on 2007-11-11
Could I not have the shared drive NTFS with NTFS-3G? Or is having an ext3 shared data drive and using FS-Driver a better choice? Again, I'm new to all this, so if I'm way off I apologize. Also, how would I go about creating the shared partition? I also have a 300GB and 500GB external drive that I generally keep for all my files such as music and video, would I have to change these at all to use them with both Ubuntu and XP as extra storage?

Edit: Forgot to mention that my external hard drives were both fat32.

---

### Post by kwacka on 2007-11-11
NTFS files are only comparatively recently read/write capable under linux, so I'd personally go for a FAT32 shared partition.

Install Windows first, then Ubuntu, and you'll find that the shared partition will show up.

Seems pretty reasonable the way you're thinking. There was a rule that swap should be double the size of RAM, but that was back when 256 MB was a lot.

---

### Post by fisting_mayfield on 2007-11-11
> **kwacka said:**
> There was a rule that swap should be double the size of RAM, but that was back when 256 MB was a lot.

I've read this before - thanks for clearing this up.  I've got a new lappy coming today or tomorrow, and was wondering if I really *needed* an 8 gig swap (double the RAM).  I think now 1 will be sufficient.

---

### Post by rsambuca on 2007-11-11
> **kwacka said:**
> NTFS files are only comparatively recently read/write capable under linux, so I'd personally go for a FAT32 shared partition.

Install Windows first, then Ubuntu, and you'll find that the shared partition will show up.

Seems pretty reasonable the way you're thinking. There was a rule that swap should be double the size of RAM, but that was back when 256 MB was a lot.
I would definitely stay away from FAT32.  Whether you want to use ntfs or ext3 would depend on what you think you will boot more.  If you thnk you will boot Windows more, than make them ntfs;  if you think you will boot Ubuntu more, then make them ext3.  FAT32 is just a terrible filesystem, and requires a lot of maintenance to run properly.

With that much storage space, it really doesn't matter what you do with the 250 drive!

---

### Post by gn2 on 2007-11-11
> **rsambuca said:**
> FAT32 is just a terrible filesystem, and requires a lot of maintenance to run properly.


And has a 4gb file size limit, so DVD .iso files are out.

---

### Post by Chaos45 on 2007-11-11
OK, that really clears up a lot of the questions I had. Thanks for the help :)

---

