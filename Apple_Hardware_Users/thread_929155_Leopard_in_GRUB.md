---
title: "Leopard in GRUB"
date: 2008-09-24
forum: Apple Hardware Users
---

### Post by Gerinych on 2008-09-24
Here's the situation.
I have Windows Vista and Ubuntu 8.04 on my hard drive. I wanted to install OSx86 (Leopard) on my second hard drive. So, I plugged in another hard drive and installed Mac on it, during the install, it formatted my second hard drive to an MBR hfs+. After the install, GRUB kicked in as usual, so I boot Ubuntu and add an entry for a Mac in menu.lst hoping that could work. It didn't. When I tried to boot Mac, it gave me an error "Partition table invalid or corrupt". I know that's because Mac formatted my hard drive to hfs+, and GRUB doesn't recognize it.
I've looked here for a while, but haven't found the answer. So my question is: how do you boot a Mac in GRUB? I don't want to use VMWare or anything, I find it confusing, and I don't think Mac would install on any other type of partition.

---

