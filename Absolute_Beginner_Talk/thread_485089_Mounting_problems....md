---
title: "Mounting problems..."
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by someguy91 on 2007-06-26
I mounted some partitions.. but everytime I start up.... the mounting is gone and I have to remount.. what do I do?

Also.. I still have another different mounting problem that's still exists in this thread. If you could help out here that would be amazing.


[http://ubuntuforums.org/showthread.php?t=484942](http://ubuntuforums.org/showthread.php?t=484942)

Thanks in advance

---

### Post by Rocket2DMn on 2007-06-26
If you keep them mounted all the the time, the best thing to do is put an entry in /etc/fstab
You can get that data for that by running
```
fdisk -l
```
There are many many threads about setting this up correctly.
Check it out, if you can't get it, post your /etc/fstab file and the output of the fdisk command above.

---

### Post by ugm6hr on 2007-06-26
This is pretty helpful:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Not 100% certain exactly what your problem is - but the link you provided suggests you haven't done the "Edit the /etc/fstab" part.

Try substituting "dev/hda1" with "dev/sda2" and "/windows" with "/media/vista" in that how-to.

Vista partitions are a bit tricky with regard to read-write support, I gather - but someone who uses a Vista dual-boot might be better placed to comment.

---

