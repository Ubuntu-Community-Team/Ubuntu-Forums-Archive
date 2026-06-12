---
title: "Installing on 2 hds"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Hex_Mandos on 2006-11-29
Hi, I'm a Windows user doing my mandatory annual formatting of my hard drives (I'm more than a year late, though... my computer is so sluggish that Ubuntu runs faster on the Live CD than XP on my HD). I decided to install Ubuntu on one of my hard drives, since I'm a bit fed up with Windows lately. I have a few questions:

1) Can I format an NTFS drive with the Ubuntu Live CD? I mean, I intend to keep one of them as NTFS, and I want to know if I can do that from Ubuntu.

2) If I'm going to use a whole hard drive for Ubuntu, do I need to partition it? If so, is it done automatically, and in that case, is there any benefit in doing it manually?

3) Which OS should I install first, XP or Ubuntu? I originally planned to do Ubuntu first (as it seems the fastest way to get the computer working) but I've read people recommending otherwise, so I'm not sure.

Thanks.

---

### Post by komaroveli on 2006-11-29
> 1) Can I format an NTFS drive with the Ubuntu Live CD? I mean, I intend to keep one of them as NTFS, and I want to know if I can do that from Ubuntu.
yes

> 2) If I'm going to use a whole hard drive for Ubuntu, do I need to partition it? If so, is it done automatically, and in that case, is there any benefit in doing it manually?
it is done automatically. unless you have specific need for partitions to be certain sizes, or you need specific mount points etc... do it automatically 

> 3) Which OS should I install first, XP or Ubuntu? I originally planned to do Ubuntu first (as it seems the fastest way to get the computer working) but I've read people recommending otherwise, so I'm not sure.
well....if you are not comfortable with command line, or you don't want to edit grub and mount windows partition manually then install windows first. then install ubuntu and then (going to your second question) choose manual partitioning. there you get chance to mount windows right form the start.

---

### Post by bodhi.zazen on 2006-11-29
> **Hex_Mandos said:**
> 1) Can I format an NTFS drive with the Ubuntu Live CD? I mean, I intend to keep one of them as NTFS, and I want to know if I can do that from Ubuntu.

Yes, but you can format with the windows CD as well....

> 2) If I'm going to use a whole hard drive for Ubuntu, do I need to partition it? If so, is it done automatically, and in that case, is there any benefit in doing it manually?

Well it is easier to use the automatic settings. Some people prefer to have /home on a separate partition.

I would advise a shared FAT partition for data as both OS can read FAT natively. 

> 3) Which OS should I install first, XP or Ubuntu? I originally planned to do Ubuntu first (as it seems the fastest way to get the computer working) but I've read people recommending otherwise, so I'm not sure.

Thanks.

It is somewhat easier if you install Windows first, but it does not matter too much. If you Ubuntu first you would need to re-install grub after installing windows.

---

### Post by tszanon on 2006-11-29
1. From live CD? Don't know, never tried.

2. Yes, you need to partition it. It can be done automatically. Do it manually if the automatic partitioning isn't what you want. It is recommended that you have at least 3 partitions: one for the root file system (/), one for /home and one for swap. Since /home is where your files will be written to, it should be the largest partition. For your information, I use:
/ -- 40GB (quite space, even for my needs)
swap -- 500MB
/home -- the rest (about 220GB)

3. Install XP first. During Ubuntu install, it will recognize XP and create an entry for it in the boot menu. If you install Ubuntu first, XP will completely ignore it.

---

### Post by gn2 on 2006-11-29
This may help: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by Hex_Mandos on 2006-11-29
Thanks for the replies. I suppose I'll just install XP first to avoid the hassle. I like the idea of having a large FAT partition, so I'll consider it.

---

