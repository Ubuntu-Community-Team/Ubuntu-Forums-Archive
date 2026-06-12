---
title: "Can i change bootloader MBR after install ?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by dense on 2007-06-05
I have 3 operating systems set up and running on my one hard drive in this order.
 Win. XP
 PClinuxOS hda5 with Lilo bootloader
  hda6 is swap and hda7 is home
 I installed the Lilo bootloader in MBR
  Now i installed Linux MINT Cassandra as 3rd system and put bootloader in the boot drive which is hda3
 Went to pclinux and did a /sbin/lilo and everything works fine.
 EXCEPT now i like Mint so well i want it to be my default system to load without having to go through the process of Lilo bootloader choosing Mint then choosing mint from the grub loader.
 Can anyone tell me if i can do this without reinstalling everything or leave it alone.
 Last, I do NOT know anything about Grub or what to enter in their command lines.
:(

---

### Post by bodhi.zazen on 2007-06-05
Grub will boot all those OS

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Boot Mint, open a terminal, type : ```
sudo grub
```

At the grub prompt type :```
grub-install (hd0)
```

Reboot

---

