---
title: "How Do I Get Rid of Dual Boot Partition"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by mogedwards on 2008-01-09
I installed Ubuntu on my laptop using a disk that created a dual boot system with Windows XP.

I had hoped to convert to Ubuntu as my main OS. However, although I have tried everything suggested, I have not been able to get my Linksys wireless card to work. Therefore, I have decided I will have to go back to Windows.

How do I get rid of the partition without losing what is already in Windows.

The problem is, all the forum threads I have found on this and other sites say you need the original Windows disk. 

Well both my P.C.'s, which were bought new from the UK's biggest retailer, came with Windows pre installed and no Windows disk. This appears to be the way these days. I have checked with friends and their P.C.'s have also come with no Windows disk.

Is there any way I can get rid of the partition. I don't have specialist software, such as partition magic and there are programmes on my laptop which I don't want to lose.

Thanks

Mog

---

### Post by milton1 on 2008-01-09
try either the gparted live CD or the parted magic live CD. Either of these should be able to erase your ubuntu partition and resize your windows partition to use the extra space. (basically, these are like partition magic, only free)

---

### Post by bumanie on 2008-01-09
> **milton1 said:**
> try either the gparted live CD or the parted magic live CD. Either of these should be able to erase your ubuntu partition and resize your windows partition to use the extra space. (basically, these are like partition magic, only free)

It is correct that these will resize the partition, but I don't believe purely resizing the partition will eliminate grub. Normally, one would get rid of grub via by xp recovery  console and the 'fixmbr' command. Without an install disk, I am not sure how you would do this (?Google third party tool). At this point I would be wary of  resizing the partition - it will potentially cause more problems than it solves, in the absence of a xp disk.

Do you have a recovery partition installed? I'm not sure whether this would work. Wait for further replies, someone else may know.

---

### Post by erfahren on 2008-01-09
why you're still able to boot windows try this utility to fix the MBR - you can run it from within Windows
[http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

---

### Post by muteXe on 2008-01-09
i didnt fix the mbr, i just made grub load up xp by default, then got rid of linux.  Okay i still get a grub screen for 2 seconds, but then it loads xp.  I know this isn't a perfect solution, and i dont know what would happen if i selected to boot up linux (seeing as it's not there anymore), but it works for me :)

---

