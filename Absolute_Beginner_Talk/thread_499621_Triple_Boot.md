---
title: "Triple Boot"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by mike102282 on 2007-07-12
What would be the best way to triple book Linspire, Freespire, Ubuntu.

---

### Post by phidia on 2007-07-12
I think it would be helpful to know how you intend to use those three distros because what might be "best" for one person could be another's worst.

I would think about partitioning 1st and decide which would be the default install (of course you can change that later by editing menu.lst) One distros grub or lilo will end up on the mbr and the others will use that grub to boot from. I find it easier or to my liking to install the "secondary" distros grubs to their respective boot partitions and use the chainloader command in menu.lst to boot them-that way each distro boots thru it's own grub. I'm sure some people would see that as obsessive but that's how I do it.

---

### Post by euler_fan on 2007-07-12
I triple boot XP, Ubuntu x86 and X86-64, so what you suggest is a little different but the following should work out okay. It is definitely possible anyway. The trick is finding the optimal way to do it.

That depends a bit, but I would say the something along the following lines makes sense . . . 

Shared swap partition (why do otherwise?)

A shared files partition (assuming there is a common partition format like ext2 or ext3 you can use on it). There's no reason to no keep things like music you may want from any/all of them in multiple places. This assumes the worst case--that you can't just set up a shared home folder. In which case do it as an extended partition within one of your others. You could even make Ubuntu and the "repo partition" part of the same extended partition

Then divide the rest into three to suit your needs, bearing in mind the previous comment. Then when you install, just put one on each.

But I'd also wait and see what some other people have to say.

Good Luck :)

---

### Post by indytim on 2007-07-12
I'm currently booting Xbuntu7.04, Kubuntu 7.04, Kubuntu 6.10 and Win2k.  I took the approach of a creating a small, dedicated parition for Grub.  I'm using the symbolic link method to maintain stability across all distro's for kernel upgrade.  Just some slight editing to accomodate additional ops if I expand beyond my current 4 ops.

IndyTim

---

### Post by Skidpad on 2007-07-12
> **indytim said:**
> I'm currently booting Xbuntu7.04, Kubuntu 7.04, Kubuntu 6.10 and Win2k.  I took the approach of a creating a small, dedicated parition for Grub.  I'm using the symbolic link method to maintain stability across all distro's for kernel upgrade.  Just some slight editing to accomodate additional ops if I expand beyond my current 4 ops.
IndyTim
How much space for grub?  If you could provide more detail on your setup, I'd appreciate it, as I am planning on at least a triple-boot on my desktop once I install X on there (been dual-booting this laptop for 6 months now).

*off-topic* Sorry to hear about the 2008 loss of F1 in Indy today, IndyTim.  Our house has 3 big F1 fans in it; a sad day for fans everywhere, and a sad day economically for you folks.

---

