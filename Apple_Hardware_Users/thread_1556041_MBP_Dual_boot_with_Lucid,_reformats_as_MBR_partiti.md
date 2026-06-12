---
title: "MBP Dual boot with Lucid, reformats as MBR partition scheme"
date: 2010-08-18
forum: Apple Hardware Users
---

### Post by furok23 on 2010-08-18
iv been researching online, but noone seems to have the same symptoms that i do. 

im unable to resize/add any partitions to my 500g hd after dual booting.

refit wont sync partition tables (obviously becuase theres no gpt to sync)

any help?

---

### Post by vociferous666 on 2010-08-27
im looking to do the same thing so ill let u kno of my experiences.

---

### Post by srs5694 on 2010-08-27
Is your disk now MBR-only? Does it successfully boot Linux? Does it successfully boot OS X? If the answer to all three questions is "yes," then you might try leaving the disk as MBR and use GParted, rather than OS X's Disk Utility, to resize your partitions.

A riskier fix might be to use [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk) to convert your disk from MBR to GPT. This is riskier because it's conceivable that one or both OSes will fail to boot after you make this change, so you might need to re-install boot loaders. After you convert to GPT, though, Apple's Disk Utility should be happy to resize HFS+ partitions. (It won't touch Linux filesystems, though; you'll still need to use GParted or some other Linux tool for them.)

---

