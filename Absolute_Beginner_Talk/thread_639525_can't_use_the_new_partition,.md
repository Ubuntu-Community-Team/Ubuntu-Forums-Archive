---
title: "can't use the new partition,"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Uncle_John on 2007-12-13
recently i decided to remove Windows from my computer. I simply formated the partition in which it was installed. I formated it with gparted. disk is now formated as extended disk and it has a partition which uses ext3.
because my first disk has been full i wanted to move some of the stuff on to the new one. i moved it,  but there was no sign of the free memory(on the first) that should become available after moving the data to the new disk. i found out that although i put data into the 
/media/hda1 - new disk, this data is actually still on my old disk. 
How can i access my new partition, i urgently need more space



PS: sorry for my english, it's a bit rusty:)

---

### Post by cotcot on 2007-12-13
I guess that you still have the ntfs partition in your fstab. It will not mount the ext3 automatically at boot.
If so than you have to adapt the fstab or mount the partition manually (sudo mount /dev/hda1 /moint-point-of-which-you-made-directory.

---

### Post by Uncle_John on 2007-12-13
thank you very much:D i also had to change the ownership of that file, but that wasn't a problem. btw, do you know what is the difference between the fstab and mtab?

---

