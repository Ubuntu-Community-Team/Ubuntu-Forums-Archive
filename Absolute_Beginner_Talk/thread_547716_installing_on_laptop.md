---
title: "installing on laptop"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by invinate on 2007-09-10
Hi i have a laptop with Windows and Gentoo that's partitioned like this:

1. NTFS with wiindows
2. FAT32 with files
3. Linux boot ext3
4. Linux swap
5. Linux ext3

I want to install ubuntu instead of Gentoo.
I currently have grub installed where i choose what i want to boot.
What steps should i take to change gentoo with ubuntu ?

---

### Post by Duck2006 on 2007-09-10
Just over write the Gentoo install with ubuntu install.

---

### Post by invinate on 2007-09-10
as you can see there are 3 linux partitions. /boot has a gentoo kernel and grub configs on it.
what will happen if i just delete these 3 partitions and install ubuntu on this free space? will grub work?

---

### Post by Duck2006 on 2007-09-10
Yes use gparted to delete the three Gentoo partitions and install ubuntu in the space where the other linux was installed. Grub will be installed with the ubuntu install

This is where you can get gparted live cd

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by invinate on 2007-09-10
ok, i see thanks, just one more question,
must i use gparted, or maybe ubuntu will ask what i want to keep/delete during installation?

---

### Post by Duck2006 on 2007-09-10
You can do it all from within ubuntu, but i fine it better to do it from the live gparted cd

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by dptxp on 2007-09-10
You can just use Ubuntu Live CD. Use the same / partition for /. That is all.
The Live CD shall not proceed unless you tick it to be formatted. Then Ubuntu
shall not see Gentoo and  make new GRUB.

---

### Post by invinate on 2007-09-10
thanks, i will try to manage from the installation :)

---

