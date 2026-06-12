---
title: "external hd in text mode"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by verdickt on 2006-12-01
hi,

i am running linux in text mode, my question

How can i find out the mount point of a freshly connected usb device ? is it sda1 , sda2 ???

Which log do i have to tail (dmesg ... ) ?? so i can mount the device ??

thanks in advice

---

### Post by Ben Sprinkle on 2006-12-01
Just try it:
```

sudo mount /dev/sda1 /mnt/sda1

```
Untill you see it.

---

### Post by verdickt on 2006-12-01
it was sdc5 in my case

how to find out quickly

just plugin the hd and then run

dmesg |tail and it showed me the latest found drives

sdc1,sdc2 and sdc5 and 5 was the fat32 partition that i needed

---

### Post by Bachstelze on 2006-12-01
```
ls /dev/sd*
```

will work too, and will be perhaps less confusing than the dmesg output.

---

