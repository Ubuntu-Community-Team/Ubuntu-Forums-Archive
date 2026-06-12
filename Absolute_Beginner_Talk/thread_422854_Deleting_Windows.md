---
title: "Deleting Windows"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by xArv3nx on 2007-04-25
Hai.

I am about to make the full switch to Ubuntu 7.04, but I need to delete my Windows XP partition. How would I go about doing that? Do I just use gParted and remove the partition? How would i go about merging the partitions?

Thanks,
Joseph

---

### Post by Seisen on 2007-04-25
You can use gparted, when you delete the windows partition it should let you merge the unallocated  space with ubuntu.

---

### Post by crav on 2007-04-25
Also, don't forget to remove windows from your boot options in Grub. The file for options is at /boot/grub/menu.lst

---

### Post by oilchangeguy on 2007-04-25
just simply allow ubuntu to use the entire drive when you install it. this will remove windows.

---

### Post by canadianwriterman on 2007-04-25
Or, you could do a full fresh install of Feisty and choose to have the install take over the HD. That's what I did this week when I finally decided to go "windowless."

EDIT: You beat me to it, oilchangeguy!

---

### Post by ubuntukid on 2007-04-25
> **oilchangeguy said:**
> just simply allow ubuntu to use the entire drive when you install it. this will remove windows.

But will also require you to re-install ubuntu if it's already installed. Simply delete the windows partition, and you should be able to resize your ubuntu partition to take up all the available space that you just freed up.

---

### Post by oilchangeguy on 2007-04-25
> **ubuntukid said:**
> But will also require you to re-install ubuntu if it's already installed. Simply delete the windows partition, and you should be able to resize your ubuntu partition to take up all the available space that you just freed up.

please read the first post. the user says they are about to make the change to ubuntu.

---

