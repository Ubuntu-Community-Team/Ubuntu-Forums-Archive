---
title: "Big Problem! Needing some assistance..."
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-08-19
I wanted to try out the newest kernel 2.6.22, so I followed the instructions in a thread found on the fourms...

The installation went fine and all that...The kernel is okay, but I wanted to go back down to my existing kernel...2.6.20-16. The problem is that during the installation of the newest kernel, it required that the gutsy versions of libc6, libc6-dev and libc-686(which ticked me off because I have x86) to be installed. The problem is literally all the programs I have require the fiesty version of libc6 and libc6-dev. I've been trying to figure out a way to downgrade...but everytime I try in Synaptic, it tells me that it's going to remove literally every program on my comp. Firefox won't work correctly with this version of libc6...how can I downgrade my packages without having to remove everything???

---

### Post by isaacj87 on 2007-08-19
bump...

Please there's got a be a simple solution to downgrading without having to remove all the programs.

---

### Post by spur on 2007-08-19
When you installed the new kernel did you delete or remove the old one?
If not you may be able to simply login in to the old one. When grub comes up press 'esc' to get a menu and choose the version with the numbers to indicate your old kernel. From then on it should be the default if not that can be changed.

---

### Post by HermanAB on 2007-08-19
Re-install.  Sorry.  If you have a separate /home partition, then re-installing is very quick and easy.

Soooo, now you know why it is a good idea to always create a separate /home partition and next time you feel adventurous, do so inside VMware, VirtualBox or Qemu, not on the base system!

Cheers,

Herman

---

### Post by isaacj87 on 2007-08-19
> **HermanAB said:**
> Re-install.  Sorry.  If you have a separate /home partition, then re-installing is very quick and easy.

Soooo, now you know why it is a good idea to always create a separate /home partition and next time you feel adventurous, do so inside VMware, VirtualBox or Qemu, not on the base system!

Cheers,

Herman

Damn...okay...

---

