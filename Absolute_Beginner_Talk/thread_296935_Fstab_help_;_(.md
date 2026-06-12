---
title: "Fstab help ; ("
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2006-11-10
Hi,

I added an additional h/d to my system.  I added the line in ftab to mount it all the time, but it doesn't work on boot.  If I use mount -a it will mount it from the command line, but not on start up.. here's the line..  
/dev/sda5       /media/drive2   ext3    defaults        0       0  ... why does it mount when I run mount -a ,but not on boot up ??
Thanks !!

---

### Post by ciscosurfer on 2006-11-10
Try [this link]("http://psychocats.net/ubuntu/mountlinux") out.

---

### Post by lloyd_b on 2006-11-10
```
/dev/sda5 /media/drive2 ext3 defaults 0 0
```

Try:

```
/dev/sda5 /media/drive2 ext3 defaults 0 2
```

instead.

Lloyd B.

---

### Post by Felipe_U on 2006-11-10
Did you add 'auto' to the options list?

---

### Post by MrKlean on 2006-11-10
Thanks guys..Umm..nope...didn't add auto.  I will now and see what happens.  I didn't add it on my other puter either, but it works there.  I'll see what happens.. Thanks again ; )

---

### Post by MrKlean on 2006-11-10
Ok.. I feel REALLY stupid !!!    I've been working on the wrong drive ; ((  I think I'm brain fried after werkin on Edgy on 2 different puters at the same time !!  Thanks for all the help !!  I'm going over to Edgy as soon as my bank can let me use Firefox to look at my accounts !!  Thanks again !!   I'm gonna stick my head in the toilet and flush 3 times LOL!!   By the way, going to that page is what made me see my mistake LOL!!  Thanks ciscosurfer !!

---

### Post by ciscosurfer on 2006-11-10
Any time!

---

