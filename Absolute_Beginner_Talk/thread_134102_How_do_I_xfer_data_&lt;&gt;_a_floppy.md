---
title: "How do I xfer data &lt;&gt; a floppy?"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by don cole on 2006-02-21
How do I xfer data <> a floppy?
How do know from the terminal if linux sees my floppy?
How do I read my floppy from thr terminal?

Don Cole

---

### Post by heimo on 2006-02-21
I've never used floppy drive with Ubuntu, but I'd first right click on upper panel -> Add to Panel, choose Disk Mounter and click on the new applet - choosing "mount floppy 1". Or in terminal:
```
mount /media/floppy
```

Now you should see a directory /media/floppy with your floppy disks content in it. Remember to unmount it before removing with the applet or command:
```
umount /media/floppy
```

I'm not 100% sure about the applet as I'm no longer using Breezy Badger.

---

