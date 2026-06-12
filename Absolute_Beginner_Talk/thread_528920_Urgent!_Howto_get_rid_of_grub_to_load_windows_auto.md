---
title: "Urgent! Howto get rid of grub to load windows automatically?"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-08-18
Hi,

I decided to use windows only on my laptop and erased ubuntu
I erased ubuntu on dev/sda2 and swap on dev/sda3, windows is on dev/sda1 and and /dev/sda4.

After erasing ubuntu on /dev/sda2, I converted that to ntfs

so now I have /sda1 (windows installed) /sda2 (empty partitioned with ntfs) /sda4 (exists my windows data files with ntfs)

I restarted compouter and windows does not started anymore since there is still grub menu. How can get rid of this menu and start windows automtically as before when I bought the laptop as fresh?

Thank you
findik1

---

### Post by overdrank on 2007-08-18
> **findik1 said:**
> Hi,

I decided to use windows only on my laptop and erased ubuntu
I erased ubuntu on dev/sda2 and swap on dev/sda3, windows is on dev/sda1 and and /dev/sda4.

After erasing ubuntu on /dev/sda2, I converted that to ntfs

so now I have /sda1 (windows installed) /sda2 (empty partitioned with ntfs) /sda4 (exists my windows data files with ntfs)

I restarted compouter and windows does not started anymore since there is still grub menu. How can get rid of this menu and start windows automtically as before when I bought the laptop as fresh?

Thank you
findik1

HI you have to use the windows cd and restore the mbr. :popcorn:

---

### Post by findik1 on 2007-08-18
how do I do that

---

### Post by splintercellguy on 2007-08-18
You have to boot the Windows CD, then go to Recovery Console. From there, just type fixmbr.

---

### Post by testube_babies on 2007-08-18
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by phenest on 2007-08-18
Jeez! Now we're helping Windows users! Poor buggers.

---

### Post by cosborn72 on 2007-08-18
Just as a side note, if you no longer have the Windows CD, you can download an iso called super grub

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

which can fix it as well.

---

