---
title: "small faux pas installing xen?"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by unabatedshagie on 2007-01-17
I thought I would give installing xen a try, ](*,) 

I followed the instructions from [here](http://tx.downloads.xensource.com/downloads/docs/user/#SECTION02120000000000000000) and downloaded [this](http://bits.xensource.com/oss-xen/release/3.0.4-1/bin.tgz/xen-3.0.4_1-install-x86_32.tgz) tgz file.

After running **sh ./install.sh** I copied all the files in the **/dist/install** folder to the relevant locations and added the following to grub ```
title Xen 3.0 / XenLinux 2.6
  kernel /boot/xen-3.0.gz dom0_mem=262144
  module /boot/vmlinuz-2.6-xen0 root=/dev/sda4 ro console=tty0
```

Now for a start the option in grub doesn't work, it says file not found but when I start ubuntu I get logged in for maybe 30 seconds to a minute before the full system freezes, the only thing that works is the mouse.

So, how would I go about getting myself out of this small predicament I now find myself in? :-k

---

### Post by Henry Rayker on 2007-01-17
when you copied the files from /dist/install, how did you do that? Did you, perhaps, copy over existing Ubuntu files?

---

### Post by unabatedshagie on 2007-01-17
I opened nautalis as root and copied them over.

In hindsight probably not the best move on my part :)

I'm guessing I'm SOL and a fresh install's in order?

---

### Post by Henry Rayker on 2007-01-18
I'm not familiar with Xen, so I'm probably not the best to provide you with help. However, I would recommend resizing your partition (the one that currently houses Ubuntu) and install again on the resized partition. This way, you can transfer all of your files without losing anything. Additionally, you can keep playing with Xen in the current partition...and either try to get it to work, or just give in and delete the partition and resize the "new" partition to take up that new space.

---

