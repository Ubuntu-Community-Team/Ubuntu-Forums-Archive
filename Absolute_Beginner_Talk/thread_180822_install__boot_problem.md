---
title: "install / boot problem"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by roderashe on 2006-05-23
hi, everyone.

my son and I are absolute beginners and need a little help. we have a dell box with 2 160GB HD's mirrored. it has win2k3 server installed but this is a box I got for free from work so I really don't care if I keep windows or not. In fact, I would prefer not to have it.

we installed from the cd and, I think, installed grub. when it rebooted, though, it went into windows and kept re-booting in some sort of terrible loop! Anyway, I don't see any option to boot into Ubuntu - it just keeps going into the 'window's boot loop'!

Any ideas? It's no big deal if we have to re-format or whatever. If we do re-format, what is the best way to do this? Thanks!!

---

### Post by adam.tropics on 2006-05-23
Hey,

Welcome to the forums and Ubuntu. This is by no means an uncommon  thing! Look [here]("http://www.ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub+live+cd") for a nice simple possible solution. Good luck!

---

### Post by Belathor on 2006-05-23
Hi,

If you don't mind loosing Windows, then I'd just make sure that when you try to install it again to delete all the partitions from the hard drives and start from scratch. There should be an option to reformat the entire hard drive if you want, or you can edit the partition tables manually. If you do that, create a separate /home partition so that your data and settings stay intact even if you have to reinstall the operating system again or want to try a different distribution. Make sure you create a swap partition too. I think the general rule is to make SWAP twice as large as the amount of RAM you have.

*** Don't forget to create a / partition, as that's where the operating system is going to be installed***

---

### Post by adam.tropics on 2006-05-23
> I think the general rule is to make SWAP twice as large as the amount of RAM you have.


About 1.5 - 2 times memory yes. Just worth noting that there have been a couple of issues with the installer picking wierd sizes for swap in the 'let ubuntu take care of partitioning' (i can't remember the exact name) option. So worth checking on the review screen before commiting changes.

---

### Post by roderashe on 2006-05-23
thanks very much for all the help.

well, I've gone through the above and linked suggestions. but, when we try to boot up, we still get 'error loading operating system'. should I be seeing a grub interface?

---

