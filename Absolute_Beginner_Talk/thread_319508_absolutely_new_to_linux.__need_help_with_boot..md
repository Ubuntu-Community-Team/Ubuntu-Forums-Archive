---
title: "absolutely new to linux.  need help with boot."
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by sjewenp on 2006-12-15
i have ubuntu and xp installed on separate drives and can't access ubuntu unless i change the boot order.  have tried f8 but only xp is showing.  how do i remedy this?

---

### Post by zgornel on 2006-12-15
> **sjewenp said:**
> i have ubuntu and xp installed on separate drives and can't access ubuntu unless i change the boot order.  have tried f8 but only xp is showing.  how do i remedy this?
Make the Ubuntu partition active.

---

### Post by sjewenp on 2006-12-15
i can't make it active.  i created the partition using the ubuntu installation.  windows sees a partition there but it's unknown and the only option in disk management is delete.

---

### Post by bulldog on 2006-12-15
Set the other hard disk as master boot device in your BIOS.
I've I'm not mistaken GRUB is installed on this disk.
Now you should be able to boot Ubuntu and windows.

If windows is not listed in your menu.lst,we can add it to it.
Just fire up ubuntu the way I suggested and type in your terminal```
sudo fdisk -l (l as in like)
``` and copy this to the forum to see how your partitions are configured.

Then ```
cat /boot/grub/menu.lst
``` to see your menu.lst and copy this to the forum as well.

---

### Post by sjewenp on 2006-12-15
i can't copy because i can't connect to the internet on my linux machine.  this is so frustrating. i was trying to do it one step at a time.  boot first, internet next.  i can't do either.  i am trying to connect through my wireless router.  i enable my wireless connection, include my wep key and my ssid. i can't get it to work.

---

### Post by bulldog on 2006-12-15
./wrong topic
./wrong answer sorry

---

### Post by sjewenp on 2006-12-15
i know, i was just venting...](*,) 
as far as dual booting, i have xp in raid0, so i can't set a master/slave configuration.
i don't want to have to change my bios everytime i wanna run ubuntu.

---

### Post by bulldog on 2006-12-15
Well if you gave all the info what is relevant in your first post,like a raid 0 and no internet connection,it should make a difference.

Now we have to deal with new problems every time.
That's not gonna help you at all.

Suggest you make a new topic with all the info,maybe someone can help you with your problems.

---

### Post by sjewenp on 2006-12-15
thanks

---

