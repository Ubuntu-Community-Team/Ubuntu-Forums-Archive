---
title: "None of my external usb storage devices mount"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Kitsun on 2007-10-21
Every time I plug in a USB drive or a MicroSD card reader Ubuntu gives me "Invalid mount option when attempting to mount the volume."

This has only happened in Gutsy, it was working fine in Feisty.

---

### Post by tommy_k on 2007-11-02
Did the same for me.

How did you install your Gutsy system? Did you use memory card instead of cd? Because I did and that was the reason of my problem - the installer did insert line into /etc/fstab saying that my card reader is cdrom. Ouch.

So check your /etc/fstab. If you don't know what device your card reader is, try this:

run terminal (Applications | Accessories | Terminal )
run command
```
 tail -f /var/log/messages
```
you will see lines like this:

```
sd 4:0:0:2: [sdd] 4019200 512-byte hardware sectors (2058 MB)
sd 4:0:0:2: [sdd] Write Protect is off
sd 4:0:0:2: [sdd] 4019200 512-byte hardware sectors (2058 MB)
sd 4:0:0:2: [sdd] Write Protect is off
sdd: sdd1
UDF-fs: No VRS found
Unable to identify CD-ROM format.
```

Now you see you device, in this case /dev/sdd1. Check /etc/fstab, and here it is:

```
/dev/sdd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

Comment out this line and you memory card should mount now.

---

