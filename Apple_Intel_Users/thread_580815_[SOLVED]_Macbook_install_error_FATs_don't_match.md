---
title: "[SOLVED] Macbook install error: FATs don't match"
date: 2007-10-19
forum: Apple Intel Users
---

### Post by hackworth on 2007-10-19
Hello, I just downloaded and started a new install of gutsy on my Macbook CD2, but when I get to the partition screen and delete the sda3 partition and make new ones, it gives me this "FATs don't match" warning, and says I should run scandisk on my disk. I tried searching about this, and the only posts I found were several years old. Has anyone run into this warning with gusty yet? if it makes a difference, I originally had an XP install on the sda3 partition i am trying to delete.

---

### Post by ripdog on 2007-10-19
I got the same message, installing 7.10 alternative i386 on my iMac 24" first gen.

Didn't appear to cause a problem, just ignore it.

---

### Post by hackworth on 2007-10-19
yeah, that's pretty much what the older threads said, too, but i thought i would check in with gusty users first. here goes nothing...

---

### Post by cyberdork33 on 2007-10-19
> **hackworth said:**
> yeah, that's pretty much what the older threads said, too, but i thought i would check in with gusty users first. here goes nothing...

I just did this last night. I think it has to do with the EFI partition. just make sure you tell the partitioner not to mount the EFI partition and ignore the error.

---

### Post by hackworth on 2007-10-19
yup! up and running now, thanks!

---

