---
title: "cannot boot into Ubuntu on Macbook 3,1"
date: 2009-03-22
forum: Apple Hardware Users
---

### Post by mobiblu on 2009-03-22
Here is my story: I install ubuntu 8.10 using the liveCD. During the installation I choose to use the whole HD--taking out OSX. Everything went smooth but when I restart it boot to a white screen and never boot to ubuntu. If I start the macbook with the LiveCD in and choose the option "Boot from Hard Disk first" I was able to go into Ubuntu. What am I doing wrong here?

---

### Post by Peasantoid on 2009-03-22
I tried this as well (replacing the entire disk with Ubuntu, that is). Not a good idea &#8212; you need *something* with which to install firmware updates and other useful items. Also, rEFIt is extremely useful. Keep an OS X partition, but make it as bare as possible. When you customize it during installation, deselect everything that can be deselected.

Not a good solution, and I plan to remove OS X completely once I figure out how to make booting work without it. So I sort of have the same problem as you.

---

### Post by pxwpxw on 2009-03-22
> **mobiblu said:**
> Here is my story: I install ubuntu 8.10 using the liveCD. During the installation I choose to use the whole HD--taking out OSX. Everything went smooth but when I restart it boot to a white screen and never boot to ubuntu. If I start the macbook with the LiveCD in and choose the option "Boot from Hard Disk first" I was able to go into Ubuntu. What am I doing wrong here?

You may be able to fix it with the linux version of refit from ubuntu -
(withou needing Mac OSX)
```

sudo apt-get install refit

sudo gptsync /dev/sda

```

which will update the MBR on the hard disk (sda) if that was the problem.

Also see the intel mac faq sticky for reinstalling grub.

---

### Post by cyberdork33 on 2009-03-22
you can also create a rEFIt CD to boot from and sync the partition tables with.

---

