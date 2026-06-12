---
title: "First Time Linux User"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by HyperZone on 2007-06-09
Hey, I just ran my Ubuntu CD and love it. I enjoy gaming and noticed Wine supported most of my games, so I'm wondering how much space on my hard drive to partition for gaming and other multi-media stuff? Thanks in advance.

---

### Post by ggaaron on 2007-06-09
It's your personal choice=) I had 10Gb for / and the rest for /home, but I had many, many applications installed.

---

### Post by xthund3rh3adx on 2007-06-09
well using WINE isnt easy. It takes time and lots of frustration to get it working fully and nicely. 

ANd as for space, just determine how much space it took up on Windows, and it should be the same...

---

### Post by Outrunner on 2007-06-09
Well, you would need about

10GB for /
512-1GB for swap, depending on your RAM. for example I have about 300 MB for swap with 1GB RAM
As much as you can for /home , usually 20GB+ (I have 41GB)

EDIT:

> **xthund3rh3adx said:**
> well using WINE isnt easy. It takes time and lots of frustration to get it working fully and nicely. 

ANd as for space, just determine how much space it took up on Windows, and it should be the same...

I'm not sure what made you say this, because it works perfectly for me with almost no configuration at all.

---

### Post by jnorthr on 2007-06-09
Hi there -
Yes, I'd agree that ubuntu on CD is tasty, so i'm looking to install on my windows98/se currently with a single partition but i don't want to toast the windows partition, just make a second part. to hold ubuntu. I cannot find an fdisk like utility that will do the trick. Looking to use superfdisk which i googled. Do i need to make the new partition a 'linux' style part. or just 'FAT32' ? I've also bin told to create a swap part. for ubuntu. Is this really necessary? Thank you all for such a wonderful bit of wizzardry.
Thanx Jim

---

### Post by Lord Illidan on 2007-06-09
> **xthund3rh3adx said:**
> well using WINE isnt easy. It takes time and lots of frustration to get it working fully and nicely. 

ANd as for space, just determine how much space it took up on Windows, and it should be the same...

Depends on what apps you are trying to use.. Starcraft works perfectly on Wine, and so does WC3...

---

### Post by Outrunner on 2007-06-09
> **jnorthr said:**
> Hi there -
Yes, I'd agree that ubuntu on CD is tasty, so i'm looking to install on my windows98/se currently with a single partition but i don't want to toast the windows partition, just make a second part. to hold ubuntu. I cannot find an fdisk like utility that will do the trick. Looking to use superfdisk which i googled. Do i need to make the new partition a 'linux' style part. or just 'FAT32' ? I've also bin told to create a swap part. for ubuntu. Is this really necessary? Thank you all for such a wonderful bit of wizzardry.
Thanx Jim

When installing Ubuntu, the GUI installation wizard will guide you trough partitioning. You'll need an ext3 partition not FAT32. Also, yes you'll need a swap partition(you don't need to assign too much, 512 should do it)

EDIT:

> **Lord Illidan said:**
> Depends on what apps you are trying to use.. Starcraft works perfectly on Wine, and so does WC3...

And Diablo II: LoD too! :twisted:

---

### Post by ggaaron on 2007-06-09
> **jnorthr said:**
> Hi there -
Yes, I'd agree that ubuntu on CD is tasty, so i'm looking to install on my windows98/se currently with a single partition but i don't want to toast the windows partition, just make a second part. to hold ubuntu. I cannot find an fdisk like utility that will do the trick. Looking to use superfdisk which i googled. Do i need to make the new partition a 'linux' style part. or just 'FAT32' ? I've also bin told to create a swap part. for ubuntu. Is this really necessary? Thank you all for such a wonderful bit of wizzardry.
Thanx Jim

For partitioning you can use gparted.

For ubuntu you need ext3, ext2, reiserfs file system, there are other, but are less popular, probably stick to ext3

And yes you have to make swap - ubuntu won't install without it.

---

### Post by jnorthr on 2007-06-09
Ok, let me get on to that.
Ta, Jim

---

### Post by HyperZone on 2007-06-09
I'm wondering how long the partition is going to take now. I've chosen my partition size and clicked forward though it's just loading. I don't think it's partitioning already, because I read a tutorial online and it said it partitions on Step 6 not Step 5. Could someone clear me up on this?

---

### Post by Enverex on 2007-06-09
Partitioning shouldn't take long at all to be honest. Depends on what it needs to do or shift around though. Personally I only have / and SWAP because I like to keep things simple (used to have /boot too but got rid of that now aswell, didn't seem necessary).

---

