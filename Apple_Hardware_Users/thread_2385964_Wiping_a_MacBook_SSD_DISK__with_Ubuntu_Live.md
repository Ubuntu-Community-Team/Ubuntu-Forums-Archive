---
title: "Wiping a MacBook SSD DISK  with Ubuntu Live"
date: 2018-02-27
forum: Apple Hardware Users
---

### Post by giobaxx on 2018-02-27
Hello guys

I'm looking for a tool in order to wipe a ssd disk in a Macbook, and i was thinking to try to use an ubuntu live CD using ***wipe*** or [I][B]Shred. 

[/B][/I]Do you think itn could work??

---

### Post by HermanAB on 2018-02-27
Well, a Mac runs BSD on a solid state disk (I am writing this on my Mac).  Therefore you have two possibilities:
a. Enable encryption, set a password and then continue using the Mac as before.  The Mac will encrypt the disk on the fly.
b. Erase the disk ONCE using dd from a live Linux memory stick.

Since it is a solid state disk, erasing it multiple times will only waste your time and reduce the life of the disk, it will not erase it any better.

---

### Post by giobaxx on 2018-02-27
We need to sent this MacBook to get it repaired, but for policy before "sent out" we need to wipe out all the disk and reinstall all after the Laptop is back.

Yes, I read today i don't need to to a secure erase in a SSD, just to be sure the command i could use is **dd if=/dev/zero of=/dev/sda bs=4096** ?

---

### Post by slickymaster on 2018-02-27
*Thread moved to **Apple Hardware Users**.*

---

### Post by giobaxx on 2018-02-27
Just found this [https://fossbytes.com/erase-disk-linux-mac](https://fossbytes.com/erase-disk-linux-mac)

It use this command:

```
*for i in $( seq 0 2 ); do dd if=/dev/urandom of=/dev/sda; done*
```

It could be a good way to wipe out?

---

