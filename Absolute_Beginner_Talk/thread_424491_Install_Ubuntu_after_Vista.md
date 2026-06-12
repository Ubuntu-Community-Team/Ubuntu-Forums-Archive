---
title: "Install Ubuntu after Vista"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by on.journey on 2007-04-26
Hi everybody,

I have following question (please respond as fast as possible :D ). Since Vista Ultimate is annoying me for many reasons I've decided to give Ubuntu a shot, not yet generally, but on this system. However, for the moment I still need Vista on the computer and will for another two month. 

Now, I'd like to install Ubuntu without messing up any of my Vista files. Under Vista I got four partitions. One's the system partition for Vista, one stores music etc. under Vista. 

I got two more partitions there, both approximately 15GB which I'd like to use for Ubuntu. Can I simply load Ubuntu on one of them without messing up Vista? How about deciding which system to boot, I guess I could use grub. Mainly though, I firstly need to know whether Ubuntu one the 15GB partition, which is ntfs at the moment would work fine?

Please help :)

---

### Post by fglrsux on 2007-04-26
yes, you can install ubuntu on an empty partition and still retain vista, i did it 2 days ago :)
don't forget a swap partition

---

### Post by Sef on 2007-04-26
> I firstly need to know whether Ubuntu one the 15GB partition, which is ntfs at the moment would work fine?


The NTFS partition will be reformatted to ext3, the default in Ubuntu.  Also the swap partition will be reformatted to swap.  Swap should be double your ram, unless you have a gb of ram, unless you do a lot of movie making or photo editing.

Note: NTFS is a proprietary file system from Microsoft.

---

### Post by on.journey on 2007-04-26
I know, I just thought I might have to mention that because it's all one harddrive, just four partitions.

Thanks already, I'm gonna get onto that now, will save the most important files anyway (sometimes I hate being a student). 

I am really a Linux virgin, I used Suse before, but that was yeeeearrrs ago.

---

