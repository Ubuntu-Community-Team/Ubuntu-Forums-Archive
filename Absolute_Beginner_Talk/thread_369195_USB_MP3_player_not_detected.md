---
title: "USB MP3 player not detected"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by rosieg on 2007-02-24
Hi,

I just purchased an Mcody M20 2GB MP3 player which is meant to work with Linux. The system should just recognise it as an external USB storage device. Problem is, it doesn't.

If I plug my memory stick into the same usb port it auto mounts and opens the file manager for me. I am a really newbie so will need hand holding for complex solutions

Thanks...

---

### Post by louis_nichols on 2007-02-24
Ca you plug it into a windows machine and see if it's mounted? There might be a problem with the device, as Linux seems to be working.

If that works on windows, try this after plugging the device:

```
sudo mount -t vfat /dev/sda*x* /mnt/*some-folder* 
```

That *x* after sda will be a number. Just press TAB there to see what's available. You may have to try them all.

---

### Post by rosieg on 2007-02-24
Ok, I've fixed the above problem (don't laugh, usb cable not fully home).

---

