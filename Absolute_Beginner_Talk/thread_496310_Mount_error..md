---
title: "Mount error."
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by blithen on 2007-07-09
I am getting an error when I try and mount a harddrive. It saying I don't have permission. I just need to know the command for the terminal to mount a drive.

---

### Post by bodhi.zazen on 2007-07-09
sudo mount .....

Or add the partition to fstab, then you should be able to mount it as a user.

---

### Post by blithen on 2007-07-09
Okay, so it came up with this.
```
mount: /media/extra is not a block device
```
What does that mean?

---

### Post by lakris61 on 2007-07-09
What command did You use?
What is the name of the device?
What kind of device is it?
Is it formatted? What file system?

---

### Post by atria on 2007-07-09
```
mount /dev/<disk_partition> /media/mountpoint
```

where <disk_patition> is the block device + partition number you want to mount. Examples are hda1, sda1, hdb2 etc.

/media/mountpoint refers to the mount directory (the place you want to access the mounted device from)

Hope that helps

---

