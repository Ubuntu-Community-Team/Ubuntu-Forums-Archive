---
title: "unable to make any changes with gparted"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by the_axiom on 2007-04-27
Hi!
I have trouble resizing my partition using gparted. When I right-click on a partition the resize button is grey. And I also noticed a lock to the right of the partitions...
Whats the matter?

---

### Post by LaRoza on 2007-04-27
The drive must not be mounted to resize or alter the partition.

Using GParted Live is easier as none of the drives are mounted.

---

### Post by the_axiom on 2007-04-27
OK ill try to get GParted Live, but exactly what does it mean by mounted?

Where do I GParted Live?

---

### Post by Toadmund on 2007-04-27
Mounted means ready to read and write, unmounted means just that, not mounted.
I think you must right click, unmount, then the locks come off, when you are satisfied and SURE you have the right partition, click 'apply'.

---

### Post by LaRoza on 2007-04-27
Mounted means it can be read. Any device must be mounted to use it. You can unmount a device, but you can not unmount the device you are using.

Most devices auto-mount. You plug in a USB drive, and it is mounted.

Just follow the directions and you'll be fine. It has a simple, easy-to-use GUI.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Remember: Backup anything essential in case some data is lost.

---

