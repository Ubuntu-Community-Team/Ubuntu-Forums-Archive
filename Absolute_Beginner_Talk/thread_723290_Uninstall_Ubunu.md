---
title: "Uninstall Ubunu?"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by CraigW on 2008-03-13
Alright so heres my problem, I installed Ubuntu 7.10 on a portable HDD, I put it on this portable drive so I could use it every once in awhile, get used to the linux enviroment, but now everytime I restart my computer I get a GRUB error, because the portable HDD isnt always plugged in, so I've decided to get rid of Ubuntu on the portable HDD, how do I do this?
Ever since I installed Ubuntu on the HDD windows no longer recognizes it as a storage device, is there a way to erase the HDD in ubuntu while running ubuntu?

---

### Post by sandysandy on 2008-03-13
> **CraigW said:**
> Alright so heres my problem, I installed Ubuntu 7.10 on a portable HDD, I put it on this portable drive so I could use it every once in awhile, get used to the linux enviroment, but now everytime I restart my computer I get a GRUB error, because the portable HDD isnt always plugged in, so I've decided to get rid of Ubuntu on the portable HDD, how do I do this?
Ever since I installed Ubuntu on the HDD windows no longer recognizes it as a storage device, is there a way to erase the HDD in ubuntu while running ubuntu?

can u post ur full system specs and configuration here.

u may try loading grub on MBR of your master hard disk. that way u should not get error.

regards

---

### Post by Oldsoldier2003 on 2008-03-13
> **CraigW said:**
> Alright so heres my problem, I installed Ubuntu 7.10 on a portable HDD, I put it on this portable drive so I could use it every once in awhile, get used to the linux enviroment, but now everytime I restart my computer I get a GRUB error, because the portable HDD isnt always plugged in, so I've decided to get rid of Ubuntu on the portable HDD, how do I do this?
Ever since I installed Ubuntu on the HDD windows no longer recognizes it as a storage device, is there a way to erase the HDD in ubuntu while running ubuntu?

try booting from a live cd and using gparted to repartition the portable hdd . after that you can get rid of the annoying grub messages by booting from a windows cd and running fixmbr from the rcovery console, or fdisk /mbr from a command prompt. (either method will restore your windows master boot record)

---

### Post by bswilson on 2008-03-13
No need to do that.  You're just "stuck" at a grub prompt.  Enter these commands to boot into another OS that is loaded on your hard drive.  Then, you can mount that external HDD and do whatever you want with it.

```
rootnoverify (hd0,0)
makeactive
chainloader +1
boot
```

---

### Post by forrestcupp on 2008-03-13
> **Oldsoldier2003 said:**
> after that you can get rid of the annoying grub messages by booting from a windows cd and running fixmbr from the rcovery console, or fdisk /mbr from a command prompt. (either method will restore your windows master boot record)

If that doesn't work for you, try using [Super Grub](http://supergrub.forjamari.linex.org/) to overwrite Grub with the Windows bootloader.  That's what I had to do.

---

