---
title: "What's /boot partition for?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Green_biri on 2007-11-25
As the title asks... N00b question, I know... :p

---

### Post by bluepowder7 on 2007-11-25
typically holds the kernel that the OS uses to talk to the hardware.  also holds the GRUB menu (the menu that lets you select which OS you want to boot into if you have 2 or more installed at the same time, like WinXP and Ubuntu).  don't need it to be a separate partition - it can be bundled with the standard /root partition.

---

### Post by Green_biri on 2007-11-25
> **bluepowder7 said:**
> typically holds the kernel that the OS uses to talk to the hardware.  also holds the GRUB menu (the menu that lets you select which OS you want to boot into if you have 2 or more installed at the same time, like WinXP and Ubuntu).  don't need it to be a separate partition - it can be bundled with the standard /root partition.

Hum... ok... it's just that I saw in a thread that it should be good to make a root, a home and a boot partition, so I was wondering if it would make any difference (As I only got Ubuntu, it's unnecessary) :D

> **Artificial Intelligence said:**
> 
**9) Have seperated partitions.**
[size=1]A good idea is to have / (root), /home and /boot[/size]
[[size=1]Read more...[/size]](https://help.ubuntu.com/community/HowtoPartition)


Thanks... :)

---

### Post by mkoehler on 2007-11-25
No, separate partitions should not be necessary for your purposes.

Cheers!

---

### Post by bluepowder7 on 2007-11-25
it CAN be handy to have them separate, but isn't at all necessary.

* having a separate /home is nice when it comes to upgrading or reinstalling an OS
* having a separate /boot is nice when your BIOS can't handle the kernels that are too far into a hard drive (want them up front)

at its most basic, you need two partitions - a /root partition and a swap partition.  from there on, you can split it up to as many partitions as you'd like.  for example, you can have /root and swap and /home all separate.  or you can choose to separate /boot while keeping /home on the same as /root.

in my case, i have /root, /home, /boot, /media/storage, and swap all done as separate partitions.  my /home is small and just houses config files and whatever the OS wants to put there.  all of my documents, downloads, etc are stuffed into a separate large /media/storage partition.  i have a separate /boot partition, but that's cuz i figure it MIGHT come in handy when i get around to going dual-boot on the laptop.  right now, it's no different than if it was part of /root.

---

### Post by fineas on 2007-11-26
Just an opinion about two cases in which a separate boot partition could be useful:
1. If you want to enscrypt the whole system.The Linux kernel needs to be found by the grub, so that computer can be booted into Linux
2. Having /boot in a separate unmounted partition, maybe provide an extra protection from malicious programs.
I am not quite sure for these statements though.

---

### Post by ukripper on 2007-11-26
you can find out your boot partion using following command in terminal:

```
sudo df /boot
```

---

### Post by hyper_ch on 2007-11-26
the only reason I use a seperate /boot partition is because everything else is encrypted on my computer ;).
The /boot partition is the only one that can't be encrypted in order for the system to get up and booting ;)

---

### Post by drs305 on 2007-11-26
For future reference, for those of you that have a separate boot partition, what size is it?

---

### Post by hyper_ch on 2007-11-26
Mine is way too big ;)

about 100 MB should be sufficient if you are not collecting a lot of different kernels ;)

---

### Post by ukripper on 2007-11-26
Mine is about 50MB. i would suggest you ahve about 500MB

---

### Post by fineas on 2007-11-26
> **ukripper said:**
> Mine is about 50MB. i would suggest you ahve about 500MB

500 MB for a /boot partition? Isn't it too much?

---

### Post by bluepowder7 on 2007-11-26
mine's 245meg, but i've made it big enough to house the kernels of many operating systems (gonna multi-boot eventually).

with just the ubuntu install, my /boot which contains the kernels and GRUB is using only 17megs of that space

---

