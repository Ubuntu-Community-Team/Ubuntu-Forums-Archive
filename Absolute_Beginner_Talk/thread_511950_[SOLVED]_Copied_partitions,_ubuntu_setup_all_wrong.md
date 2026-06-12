---
title: "[SOLVED] Copied partitions, ubuntu setup all wrong"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by cawill on 2007-07-28
I copied my home and root partitions to another harddisk and created another swap file. I also restored grub so it loads up the new partition. I haven't deleted the old partitions yet, but when I boot up the new copied partition it doesn't mount a home directory, so I cant even open terminal in gnome.

How do I fix my setup so I can delete the other partitions and mount everything to the correct place?

Thanks in advance, Chris

---

### Post by coffeecat on 2007-07-28
You need to edit /etc/fstab. An added complication with Ubuntu is that it uses UUIDs to reference partitions. How confident are you to edit fstab? If you are unsure, post the contents of your fstab and your partition layout and someone should be able to help.

---

### Post by cawill on 2007-07-28
Ok, I've edited the UUID's now and everything works. Thanks for your help.

---

