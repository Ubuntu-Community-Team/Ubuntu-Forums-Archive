---
title: "changed dvdrom - now not working?"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by moredhel on 2007-07-16
my old dvd rewriter died, i then replaced it, and it is not mounting, giving the error:

```
mount: special device /dev/hdb does not exist
```


I checked the jumper, and the ide cables, that's all good.

So i presume it's something to do with fstab, though i cannot remember where that is or what to do.

Thanks in advance :)

---

### Post by moredhel on 2007-07-16
Bump

---

### Post by yabbadabbadont on 2007-07-16
What is the output when you run, in a terminal window: ```
dmesg | grep -i dvd
```  Also post the contents of your /etc/fstab file.

---

### Post by tkdolphin on 2007-07-16
The file fstab is located in the /etc directory. I'm not sure what you would have to change in that file. I recently changed from a CD burner to a DVD burner without having to make any changes to fstab. 

Check your jumper again. Make sure it is set like the old drive. Make sure all cables are securely connected. If the drive is used or old, it could be a bad drive. If its new, it could still be a bad drive or the firmware may need to be updated.

---

