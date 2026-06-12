---
title: "Urgent - 4 Partitions"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by daxLeet on 2006-11-04
I'm on the live disc for Edgy, and I already have four main partitions.


I don't know whats on them as this is a DELL computer, and I don't want to mess up anything.

Is there a way to see whats on each partition?

---

### Post by JoeMcC00L on 2006-11-04
Yes! What you need to do is mount these drives onto mount points to see them. Here is what you do:

Note which hard drive you're looking at. Look for something like hda, hdb, hdc, etc. (note, if it's a serial-ata hard drive it might be sda, sdb, etc.) The ubuntu installer should list this information somewhere when you view the partitions. If you can't find the information go ahead and go to the next step and assume it's hda. If that doesn't work, try hdb, etc. (trial and error)

Next you're going to create the mount points in your media folder. Open up a terminal and type "sudo mkdir /media/hda1". Do this for hda2, hda3, and hda4.

Next you're going to mount the drives at these mount points. Open a terminal and type "sudo mount -t auto /dev/hda1". Again, do this for hda2, hda3, and hda4.

If all went well you should have four icons on your desktop showing your hard drives. You can open these up and see what's inside.

---

### Post by ReaderRat on 2006-11-04
If you want to see what is on them filewize, run this in Terminal
```
cat /etc/fstab
```

---

