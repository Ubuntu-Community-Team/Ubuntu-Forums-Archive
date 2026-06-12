---
title: "Slave drive won't stay mounted"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by MoonTeC on 2007-02-04
Hi,
My slave drive will not auto mount at start up, i have to mount it manually through termianl
I added this to the fstab,

# /dev/hdb1 
UUID=8bc2c0e7-b680-4198-a137-0983a9b27e54 /media/store ext3 defaults 0 0

but doesn't seem to work, any hints

---

### Post by ajmorris on 2007-02-04
> **MoonTeC said:**
> Hi,
My slave drive will not auto mount at start up, i have to mount it manually through termianl
I added this to the fstab,

# /dev/hdb1 
UUID=8bc2c0e7-b680-4198-a137-0983a9b27e54 /media/store ext3 defaults 0 0

but doesn't seem to work, any hints

try this

/dev/hdb1      /media/store    ext3 defaults         0      0

( the UUID usually changes each time and is not required. Also you had *# /dev/hdb1* You should not have the *#*. Hope that helps.

---

### Post by MoonTeC on 2007-02-04
Five restarts and it's mounting!
Thank you.

---

