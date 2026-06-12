---
title: "How to delete Linux Mint?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by I_R_LEENUCKS_MAN on 2008-04-08
So, Linux Mint has commandeered my GRUB, it 0wned one of my partitions, and I'm really sick of it. Whenever I boot Ubuntu I get a disk check error when checking Linux Mint's partition, so I want to uninstall it.

How do I do that? Can I do it from Ubuntu?

---

### Post by bartcramer on 2008-04-08
Maybe it is helpful to indicate what your partitions look like by typing fdisk -l in the command line, and post the output, along with an explanation which partitions are owned by Ubuntu, Ubuntu Mint, and maybe other OS's.

---

### Post by mgranet on 2008-04-08
You can use your GParted in your LiveCD to remote the partition that Mint is on.

---

### Post by I_R_LEENUCKS_MAN on 2008-04-08
> **mgranet said:**
> You can use your GParted in your LiveCD to remote the partition that Mint is on.

Will there be any references to it in GRUB or anything?

It seems like a Linux MINT GRUB is installed, if I delete linux Mint's partition, will that go and make my system 0wned?

---

### Post by plucky on 2008-04-08
From you previous post you are getting an fsck error 8 when booting Ubuntu.

This is usually caused by the UUID of the partitions where you installed Mint changing from the ones in fstab file of Ubuntu.

In a terminal ```
blkid
cat /etc/fstab
```

If you compare the **UUID** for each partition you will find one or maybe two are different.The correct UUID is given by the blkid command.To change the UUID you need to edit the fstab file with the command in a terminal window ```
gksudo gedit /etc/fstab
``` and then copy and paste the correcty values from the blkid command into the fstab file.

If you do this correctly then the error should go away.Be careful with the **fstab** file as it is important system file.It might be good idea to make a copy before attempting to edit it.

Any problems post the output of the **blkid** and **cat /etc/fstab** cammands so we can take a look.


Good Luck

---

