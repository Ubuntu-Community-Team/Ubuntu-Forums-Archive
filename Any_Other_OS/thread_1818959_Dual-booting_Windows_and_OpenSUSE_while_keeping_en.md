---
title: "Dual-booting Windows and OpenSUSE while keeping enough room for games on Windows?"
date: 2011-08-05
forum: Any Other OS
---

### Post by Quadunit404 on 2011-08-05
I'm going to switch to OpenSUSE over the weekend (yes, I'll still come here, I'll be running Ubuntu in a VM so I can still help in threads that haven't asked something that has been answered *5000 times already*) and I've been wondering how to set up a dual-boot between Windows and OpenSUSE while having enough room for games on Windows and enough room for everything else on OpenSUSE. Remember, PC games often take up 8GB or more on your hard drive, which is why it's part of the question.

I'm wondering if maybe I should give the majority of the hard drive space to Windows (at least 300GB) and then about 150 - 200GB to OpenSUSE? I'm not really going to use up a whole lotta space on OpenSUSE (based on how I've only used about 65GB/225GB on Ubuntu) and as I said, PC games take up a LOT of space. Any help on this would be appreciated.

---

### Post by NightwishFan on 2011-08-05
Perhaps keep a shared NTFS data partition with all the files you might want to use on both opensuse and windows? Then allocate around 20gb for the / of opensuse and the rest for Windows.

Edit: Oh yeah 2gb for swap partition also, though you could use a swap file.

---

### Post by Quadunit404 on 2011-08-05
I have two external hard drives, one is 1TB (which I use for backups and storing game mods and things like that) and the other is 500GB (which I use for other things) so I already have methods of sharing between Windows and Linux.

I've been thinking maybe 20GB for OpenSUSE's / partition, 150GB for the /home partition and the rest for Windows now. A 2GB swap partition is something I'll consider, but seeing how I have 4GB RAM and I'll be upgrading to 6GB in a few weeks...

---

### Post by x-D on 2011-08-05
You have a 500GB HD, you say?...

Then, I would say:
400GB Windows - NTFS

88GB openSUSE - ext4? LVM? Whatever they use...

12GB swap partition - seeing as you're upgrading to 6GB of RAM, and they recommend double the amount of RAM you have in a swap partition! 

Hope this helps :)

---

### Post by NightwishFan on 2011-08-05
> **x-D said:**
> 12GB swap partition - seeing as you're upgrading to 6GB of RAM, and they recommend double the amount of RAM you have in a swap partition! 

Hope this helps :)

I know you mean well but this was true perhaps back in 2002. :) If you use ram heavy apps and want to hibernate perhaps using 1.2x your amount of ram is ok. I would use only around 2-3gb swap partition max otherwise. Less if you never hibernate. But I would have one, swapping is useful even on 8gb systems.

---

### Post by Quadunit404 on 2011-08-06
> **x-D said:**
> You have a 500GB HD, you say?...

Then, I would say:
400GB Windows - NTFS

88GB openSUSE - ext4? LVM? Whatever they use...

12GB swap partition - seeing as you're upgrading to 6GB of RAM, and they recommend double the amount of RAM you have in a swap partition! 

Hope this helps :)

I think I'd fill that 88GB rather quickly... I mean after all I have 65GB of data in my home folder right now and when I jump ship that 65GB will be going into OpenSUSE's /home partition. The RAM upgrade won't be until after next week AND after the RAM arrives, too. Right now I'm at 4GB DDR3 and will remain so until the new RAM arrives.

@NightwishFan: My laptop usually hibernates when I take it between classes at school and over the weekends (but I'm usually booted into Windows all weekend so that part doesn't really matter :P). I do know that suspension on the Samsung NP-RF510-S01US works as intended on every kernel since 2.6.37.

---

### Post by el_koraco on 2011-08-06
If I were doing any kind of dual boot, I'd make a relatively small / partition for Linux, not separate /home, but make a large NTFS storage partition to mount as /data or whatever. I'd then put my /home folders (Music, documents and whatnot) on the storage partition, and symlink them to /home. That way, all your data is completely separated from the OS itself, but all your config files are readily accessible.

---

### Post by Quadunit404 on 2011-09-20
I've decided.

Since Linux has mediocre performance on my laptop compared to Windows, I'll be copying what I want from Ubuntu to Windows, then remove it and merge the freed space into Windows through the built-in partitioning tools that come with Windows. I'll still use Linux, but only under virtual machines or this tablet I'm getting later on this year. And yes, I'll still be here, seeing if I can help out in some way (if I consider it worth my time) or just to waste my time :P

---

