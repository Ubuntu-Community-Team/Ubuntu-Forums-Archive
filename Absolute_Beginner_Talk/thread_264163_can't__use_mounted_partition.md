---
title: "can't  use mounted partition"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by alooma on 2006-09-24
how can i use mounted partitions with my user account ?:confused:

---

### Post by docshawnc on 2006-09-24
Well, let's see what you're working with - what does this bring back?

cat /etc/fstab

---

### Post by bulldog on 2006-09-24
> **alooma said:**
> how can i use mounted partitions with my user account ?:confused:

Yes we can work with soooo much info.

Basicly what do you want to do with them.

If they are NTFS you can only read them and copy stuff to your /home location,but writing is not aloud by default.

---

### Post by alooma on 2006-09-24
when l open folders l see noting mounted folders are empty and they have locked icon
l only use them by typing "sudo nautilus"

---

### Post by bodhi.zazen on 2006-09-24
This should be a simple fix.

You will need to edit /etc/fstab.

```
sudo gedit /etc/fstab
``` & post contents as requested above.

---

### Post by bulldog on 2006-09-24
> **alooma said:**
> when l open folders l see noting mounted folders are empty and they have locked icon
l only use them by typing "sudo nautilus"

Besides what bodhi.zazen asks you to do,what happens when you just click computer [not sudo]

Do you see your /media with your partitions and cd-rom etc?

What happens when you click a partition,does it opens and what do you see?

---

