---
title: "wondering about partitions and stuff"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by pooper on 2007-06-25
hey new to ubuntu so be gentle...

right i have a second hd installed (internal) and used gparted to delete partitions on it and make one big 114 gb partition format ext3. is this safe to do, just wondering because im used to windows and fat32s can only handle around 30gb partitions right ?

i also left a little bit on the end of the 2nd hd and made a linux-swap format partition. will this even be effective though? 

and another thing. when you want to access the 2nd hd do you always have to mount it? i found a guide to have it permanently mounted anyway. just wondered if im doing this stuff right :-k

---

### Post by Rocket2DMn on 2007-06-25
Hey, welcome to Ubuntu.  Your partition should be just fine.
Having a swap on a separate hard drive can actually improve performance when your primary HD is reading/writing.  Ubuntu needs to be actually using the partition though - I'm not sure how you go about that (or if it's automatic).
If it's an internal HD, you shouldn't have any problems having it permanently mounted through the /etc/fstab file - sounds like you got a guide for this already.

---

### Post by pooper on 2007-06-26
thanks for the response.
does any one else know anything about the linux-swap file ?

---

### Post by pooper on 2007-06-27
oh and is it safe to shut down the computer while the internal hd is mounted or should it be unmounted first ?

---

### Post by Rocket2DMn on 2007-06-27
You can shut down while any drives are mounted.

---

### Post by Nythain on 2007-06-27
part of the shutdown process includes unmounting filesystems... so no you dont have to unmount it first... i would definately add it to the fstab so it gets mounted at boot, and that should resolve the swap problem

---

