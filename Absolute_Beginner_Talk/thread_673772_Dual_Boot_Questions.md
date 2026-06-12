---
title: "Dual Boot Questions"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by airportlounge on 2008-01-21
Hello folks,

I am in quite the predicament here regarding my attempts at install a windows xp partition. Why do I want to do this? Mainly because I couldn't get a lot of my games to run. I have made a rather small xp partition successfully, but now I am having trouble configuring grub to be able to load to xp. I have sort of made a mess of my hd as well. I tried to create free space from a swap space i made too large and it as stuck in the extended partition. I thought it would automatically go to a free space pool (I know, stupid).

When I try and booted initially it said something like "(hd 0,4) unrecognizable format, make active or something like that. Truth is, my hd has so many little partitions going on, that I don't know what my windows xp hd location is (hd 0,?). Is there any way to find this out?

Heres a post of my menu.lst after the end default options:

title           Windows XP 	
root            (hd0,0)
makeactive
chainloader     +1 

Thank you very much for your time, consideration and help,

Ryan

---

### Post by airportlounge on 2008-01-21
P.S. 

I should mention, though it may seem obvious, that it will not boot into xp. Whenever I change the hd in the menu.lst it doesn't seem to work. I select the windows xp, but it always gives me an error stating that either the hd isn't found or what I said in my previous post.

---

### Post by smartboyathome on 2008-01-21
I would say if your HD is so messed up, back up everything you need and nuke it. install XP first, then Ubuntu.

---

### Post by airportlounge on 2008-01-21
ah, so what would be the most efficient method in nuking? Please don't say gparted, it took soooo long to do the partitioning grrr! :P haha

Thanks for the prompt reply!

Ummm, but aside from that, which is definitely under consideration...what do you suggest I do to find out where the windows hd (#,#) is?

Thanks again,

Ryan

---

### Post by airportlounge on 2008-01-21
b-u-m-p

---

### Post by tojge on 2008-01-21
Can you boot into your Linux (presumably, (K)Ubuntu), installation?

---

### Post by torgrot on 2008-01-21
Well if you only made the ntfs partition that isn't enough to boot windows.  You actually have to install windows to do that and that will mess up your mbr and you won't be able to boot Ubuntu.  You can fix that, but Windows will want to install to the first partition on your first hard drive.  I would say that at this point you would be better reinstalling windows and then grub.  Back everything up that is important.  Boot off the windows CD and install it.  Then boot off the Ubuntu liveCD and instal that.

torgrot

---

### Post by airportlounge on 2008-01-21
yes sir/ma'am I can boot into ubuntu just fine. My grub, so I'm assuming ubuntu as well, is located at hd (0,2)

---

### Post by airportlounge on 2008-01-21
Actually, I got grub to work just fine, its just a configuration issue, my only problem is loading xp, its all installed and all that jazz :p Thanks for the reply!

---

### Post by airportlounge on 2008-01-21
Also, referring to my previous question...What is the most efficient way to remove a linux parition ie. Make my hd all one partition again...just gparted?

---

### Post by tojge on 2008-01-21
Could you perhaps paste the output of the following command:

```
sudo fdisk -l
```

---

### Post by airportlounge on 2008-01-21
b-u-m-p

---

### Post by airportlounge on 2008-01-21
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ed69211

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             193         441     2000092+   5  Extended
/dev/sda3   *         442       13318   103434502+  83  Linux
/dev/sda4           13319       14592    10233405    7  HPFS/NTFS
/dev/sda5             402         441      321300   82  Linux swap / Solaris

Disk /dev/sdb: 259 MB, 259522560 bytes
65 heads, 32 sectors/track, 243 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         244      253424    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 64, 32) logical=(243, 44, 32)

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf733f733

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161    7  HPFS/NTFS
ryan@StaticTemple:~$

---

### Post by airportlounge on 2008-01-21
? bump.

---

### Post by tojge on 2008-01-21
Well, from what you've said, I'd say you installed Win into /dev/sda4, or, in GRUB-lingo, hd(0,3)

---

### Post by airportlounge on 2008-01-21
Well, in my lingo, "Thank you, thank you, thank you!" It worked :)

---

