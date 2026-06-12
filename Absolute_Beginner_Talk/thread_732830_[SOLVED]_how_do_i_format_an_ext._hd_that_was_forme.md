---
title: "[SOLVED] how do i format an ext. hd that was formerly used as ubuntu os?"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by hovzio on 2008-03-23
hi, i finally managed to install a dual boot on my laptop resizing partitions and so forth.The whole time I had ubuntu running on an external hd but this was getting tiresome since i use   ubuntu 99% of the time.so i put it next to ms.now i have this external drive with 3 partitions (swap and so forth) and id like to reformat it to one partition so that i can use it for backup ect...ive checked it out in gparted but there is a lock in front of the main filesystem and it wont let me make any changes.I have access to the folders in nautilus and can access everything so i guess i could just erase everything although somthing tells me thats not the way to go.do i have to change ownership or somthing like that?im relativley new to linux and would appreciate any help.

---

### Post by talsemgeest on 2008-03-23
It tells you why it is locked on gparted. Can you tell us please?

Could it also be that the filesystem has not been unmounted?

---

### Post by hovzio on 2008-03-23
the drive seems to be mounted properly, i can only see a lock in front of the partition. (in gparted) can you tell me where it tells me more on why its locked.cant seem to find any explanations.

---

### Post by talsemgeest on 2008-03-23
You can't mess with a partition until it is unmounted.

The easiest thing to do is to boot off the ubuntu cd and use gparted from there.

Oh, and to find out whats wrong you right click the partition and click "information"

---

### Post by housam on 2008-03-23
You have to [[COLOR="Red"]_unmount the ext3 _[/COLOR]]("https://help.ubuntu.com/community/Mount#head-e2cd6350c74b57c36be49bc816c54f38a319e873")format partition to enable reformat or delete. 
Or just download [[COLOR="Red"]_the newer version of Gparted _[/COLOR]]("http://gparted-livecd.tuxfamily.org/")and burn it to a cd and boot from it as a live cd and use it to delete the ubuntu partition

---

### Post by hovzio on 2008-03-23
thanks, that worked.i just used a live cd and it that did the trick.thanks alot.

---

### Post by talsemgeest on 2008-03-23
No problem, glad you got it working.

---

