---
title: "dual boot on differnet hard drives"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by prophet11 on 2006-07-07
I was wondering if you can install Ubuntu on a differnt hard drive then the one you have XP on..?

I have xp on my main hd then i have a 80 gig for differnt stuff then i have a 9gig ntfs formated hd that is totally empty its just sitting there i came across Ubuntu at work looks intersting soo i was wondering how would i install it on the 9 gig HD and dual boot to XP and U if they are on differnt HDs?


](*,)

---

### Post by sumitsen on 2006-07-07
Hi prophet11,

The way I understand your problem is that, you have already installed windowsxp on one drive and now want to install ubuntu on a 9GB drive seperate drive. No problem. You can install that.

FIrst go to the bios and change the hard disk priority to make 9GB hdd to be the first one to load.

Then install the ubuntu from the live cd.

It will automatically detect the drives and install ubuntu on the 9GB hdd and grub will be loaded on the same disk.

Finally when everything is installed, in the grub menu you will have the ubuntu as well as the windowsxp to boot from.

Cheers, Sumit

---

### Post by prophet11 on 2006-07-07
sounds streight forward, the tutorials made it seem VERY complicated.. 

Ill do it tommrow i have to burn it.

---

### Post by Arisna on 2006-07-07
Note that you may need to add something along the lines of the following to the XP entry for it to boot:

```
map (hd0) (hd1)
map (hd1) (hd0)
```

This assumes you have two IDE hard drives in the setup described above.  It makes Windows think it is on the first hard drive.  You may or may not actually need to do this, but I wanted to get this out in the air early just in case.

---

### Post by prophet11 on 2006-07-07
i have no idea what that means

---

