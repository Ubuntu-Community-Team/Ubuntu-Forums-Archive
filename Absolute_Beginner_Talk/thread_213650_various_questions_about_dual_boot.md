---
title: "various questions about dual boot"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by syedn on 2006-07-11
i've only been playing with ubuntu for a few weeks now, but i'm already 'seeing the light' as it were.  i really like this kind of environment as opposed to windows.  there is very little windows-exclusive type applications that i use any more so i've been contemplating dual booting for this coming semester of schooling.

so i'm guessing the best setup would be a linux/xp/fat32 split.

a question i have though: how big would i want each partition to be.. and when you install programs on linux, is there a way to select where they go?

at least to me it seems like i have no control over that though i'm sure i do and am just too new to know how, haha.

anyway i'm just thinking in advance for partition sizing and such (and if say somewhere down the road i need to blow an install away for a newer distro or an entirely different one, etc)

any advice or thread links or anythign on the subject (in general too) would be amazing.

thanks a bunch!

---

### Post by aysiu on 2006-07-11
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by syedn on 2006-07-11
thanks, i'll check into that!

---

### Post by syedn on 2006-07-11
i had another question and i just remembered it:

my system (the newer one anyway) is 64-bit amd dual core.

was wondering .. is it wiser to put ubuntu 64 or 32 bit on it?

i know that i've read there are various problems with some of the 64 bit support.. so which am i going with here?

---

### Post by BIZKeT on 2006-07-11
> **syedn said:**
> i had another question and i just remembered it:

my system (the newer one anyway) is 64-bit amd dual core.

was wondering .. is it wiser to put ubuntu 64 or 32 bit on it?

i know that i've read there are various problems with some of the 64 bit support.. so which am i going with here?


Same question here. I am going to be usning Cedega on it and I am not finding alot of info for it in a 64 bit setting.

---

### Post by Emceay on 2006-07-11
I have a 64 and it didn't install the 64 bit version so neat, the two times I installed using the 32 bit there were no hangups excluding windows.

I see the 64 bit version being a worse deal at the end of the day. Even if it's a little faster, no point in speed if there's nothing to make speedy.

---

### Post by syedn on 2006-07-12
so you're recommending at the moment -- install 32bit ubuntu?


let me rephrase my question a bit in this edit:
I'm attempting to switch over to using Linux for all but gaming at school.  What do you all think would be the best way to partition my harddrive for said setup?  Should I have a shared partition.. what file system should it use, etc?

Thanks!

specs on pc:
amd x2 3800
2gb ram
160gb hitatchi
nvidia geforce 7800 gtx

side note: a good friend of mine has recommended for what i'm currently doing to use a distro like fedora or suse as opposed to ubuntu?  any comments on that?

---

### Post by richbarna on 2006-07-12
The ideal partitions would be:-
Xp + Grub|Ubuntu /root|Shared Fat 32|Swap

You choose what you want for Xp, Ubuntu and Shared FAt32
Swap should be around 512Mb depending how much RAM you have. Some people with low RAM have 1Gb of Swap, some people with 1Gb+ of RAM have no Swap at all.

Remember that you can only have 4 Primary partitions on one disk.
However if you create an extended partition, you can put as many logical partitions as you want inside it.

Do not put Windows Xp inside an extended partition as logical.
Life is much easier if windows is on the first partition on the First drive.
Windows should always be installed first.

---

### Post by indytim on 2006-07-12
If you're going to partition before you install and you've got unused portions of the drive, set up your common share between Window and Linux with a FAT32 partition.  I'm going to be off-line in a few minutes but the collective can give you good advice on size if you provide feedback on how big the drive is and how much window related files you have that you will need to retain.

IndyTim

---

