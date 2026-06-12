---
title: "Swapon doesn't turn swap on?"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-02-22
Hi there,

I installed Ubuntu without any swap space(I have a gig of mem) but now I want to give Ubuntu some swap space. I have portioned part of my drive with the swap file system and I have issuede the command: sudo swapon -a.

When I now open up KSysGaurd it doesn't see the extra swap memory and still says no swap space available? 

Do i have to mount the swap partition first?

Thanks,

Rudolf

---

### Post by mcduck on 2007-02-22
You'll have to do it this way:

1. run 'sudo mkswap /dev/<yourswappartition>' to create swap on the partition.
2. run 'sudo swapon -a' to activae swap
3. run 'sudo nano /etc/fstab' and add a line like '/dev/<yourswappartititon> none swap  sw 0 0', then press Ctrl-X to exit and answer 'y' when nao asks if you want to save the file. This will make your swap work automatically from this on.

---

### Post by anaconda on 2007-02-22
you could also just make a swap file.. swap doesnt have to be a separate partition..

link:
[http://www.ubuntuforums.org/showthread.php?t=265051&page=2&highlight=swap+file](http://www.ubuntuforums.org/showthread.php?t=265051&page=2&highlight=swap+file)

---

### Post by RudolfMDLT on 2007-02-22
Thanks anaconda bu I've already formatted the thing! :)

Mcduck - thanks, I'll try this!

---

### Post by RudolfMDLT on 2007-02-22
mcuck - Thanks! works!:)

---

