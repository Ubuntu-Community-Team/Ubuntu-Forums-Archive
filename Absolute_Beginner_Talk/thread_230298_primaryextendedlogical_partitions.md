---
title: "primary/extended/logical partitions?"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-08-05
Ok, I made it as far as the partition step of the installer and how to back out with yet another question (probably my final question!). I was faced with the choice of making the partitions either primary or extended, and not knowing what extended meant (and also you can't choose a file system type with it), I chose all primary. But I couldn't make more than four of these, so I figured something was wrong.

Based on this [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html) it looks like I want to make Windows my primary, make the rest of the space extended, and then within the extended partition make my other drives logical. Is that correct? Will I be able to have four logical drives in my extended partition? Do I need to make any of them (the / partition, for example) primary as well?

Also, does the / partition need to be a primary partition that is not a part of the extended partition (so it's basically 'parallel' to the Windows partition)? Or does any of this really matter in terms of functionality?

Thanks! I'm almost on my way to using Ubuntu tonight! :)

---

### Post by reacocard on 2006-08-05
> make Windows my primary, make the rest of the space extended, and then within the extended partition make my other drives logical
That's what i use. works perfectly. windows should already be primary, so don't mess with it. you can have as many partitions as you want in an extended partition (i have 6 in mine). my / is in the extended as a logical partition. you should use the ext3 filesystem for your ubuntu partitions (except swap, which should be (surprise) linux-swap.) I'm attaching a picture of my setup so you can see what it looks like. the partitions are (in order):

Quickplay (for playing dvds without booting, you won't have this)
Extended
-/boot
-/
-/var
-swap
-/home
-/media/extra (misc stuff)
Windows (this will probably be at the beginning for you)

Hope this helps!

---

### Post by JohnJSal on 2006-08-05
Thanks a lot! I'm going to do this now!

---

### Post by kinematic on 2006-08-05
> **reacocard said:**
> you can have as many partitions as you want in an extended partition

well actually,you can't.
linux supports up to 63 extended partitions on an ide drive and upt to 16 on a sata drive.

---

### Post by reacocard on 2006-08-05
> ...up to 63 extended partitions on an ide drive and upt to 16 on a sata drive.
I stand corrected. Still, its unlikely you would ever need 63 partitions.

---

