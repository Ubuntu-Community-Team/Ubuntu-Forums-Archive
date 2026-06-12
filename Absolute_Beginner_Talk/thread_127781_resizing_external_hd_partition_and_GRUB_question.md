---
title: "resizing external hd partition and GRUB question"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by RaiSuli on 2006-02-09
Hi,

I have a 200gb external hd that's been formatted as a single fat32 partition. I'd  like to shrink this partition with gparted and add an ext3 one. Will this mess up my GRUB settings, and is there anything else I need to be aware of?

---

### Post by frodon on 2006-02-10
I don't think so, you will just need to add a line in fstab to mount your new partition on startup but nothing will be broken with GRUB.

---

### Post by TrendyDark on 2006-02-10
I wouldn't imagine you installed Ubuntu on an external HD, so it shouldn't mess with your settings at all.

---

### Post by StefanoCole on 2006-02-10
I did the same operation as you and everything went fine. Note: unmount the partition you are going to shrink.
Second note: the new ext3 partition that I created with gparted had root as owner, and I was not able to read/write in it from my user account. To do it I had to change permissions with "sudo chmod".

Stefano

---

### Post by cotcot on 2006-02-10
Installing Ubuntu on a USB HDD is not as easy as on an internal HDD. You need to modify the kernel which looks to me as guru's stuff when read about it.

---

