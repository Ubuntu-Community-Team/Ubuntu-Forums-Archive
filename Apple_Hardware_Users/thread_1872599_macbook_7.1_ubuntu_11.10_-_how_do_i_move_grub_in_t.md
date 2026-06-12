---
title: "macbook 7.1 ubuntu 11.10 - how do i move grub in the linux partition ?"
date: 2011-10-31
forum: Apple Hardware Users
---

### Post by ytzejam on 2011-10-31
[B]Macbook pro 7.1
triple boot using rEFIT
-Ubuntu 11.10
-Leopard
-Win7[/B]

HI ALL!!!
i recently installed ubuntu 11.10 on my macbook (new installation from cd), all perfect, but by mistake, i've installed GRUB into the default partition instead of the linux one. this gives me some little issue

here is the fdisk output
```


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          39          19+  ee  GPT
/dev/sda2              40      409639      204800    b  W95 FAT32
/dev/sda3          411648    49238015    24413184   83  Linux
/dev/sda4   *    49238016   133363711    42062848    7  HPFS/NTFS/exFAT


```

there's also the leopard partiton and the swap partition, but fdisk won't recognises it...

whatever, the point is
1 how can i precisely determinate in which partion grub2 is
2 how can i move grub from his partition to the linux one

help plz !
thanx yoe ;)

---

### Post by ytzejam on 2011-11-03
:(

---

### Post by rahuldroy on 2011-11-06
have you tried holding down option button on boot???

---

### Post by ytzejam on 2011-11-11
mmm nope... what do you mean with boot menu ? rEFIT or grub2
i try to explain what happens

my previous configuration (the working one) gave rEFIT splashscreen at the machine startup, with the three options (leopard - ubuntu - windows) 
chosing leopard or windows it loaded directly the requested os, meanwhile chosing ubuntu it loaded grub and then ubuntu, and that was perfect.

Now i got the anyway rEFIT splash screen at the machine startup, chosing leopard it goes directly but chosing windows, it goes on grub, and there i gotta chose windows again. no problems with ubuntu (of course) !!!

---

