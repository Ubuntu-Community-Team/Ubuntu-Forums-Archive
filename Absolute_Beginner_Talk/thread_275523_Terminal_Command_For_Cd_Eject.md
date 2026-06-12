---
title: "Terminal Command For Cd Eject"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by firebirdworks on 2006-10-11
What is the terminal cd eject and the command to bring the cd back in?

---

### Post by aysiu on 2006-10-11
I don't know about bringing it back in, but the eject command is *eject*: ```
sudo eject /dev/cdrom
```

---

### Post by Kateikyoushi on 2006-10-11
You can eject it with the eject command.

---

### Post by steve.horsley on 2006-10-11
**eject** should open the tray
**eject -t** should close the tray
On my system, I don't need to use sudo, and I don't need to give the device name. I guess I would have to give the device name if I had more than one drive.

---

### Post by Kateikyoushi on 2006-10-11
Yes sudo is not necessary, I guess because the user is in the cdrom group, and the path can also be omitted if have only one optical drive.

---

### Post by llama320 on 2008-06-03
just found this thread, checked out the man file, and realized a cool little thing you can do with eject

```
eject -T /dev/cdrom
```

This will eject the disk tray if it is closed, and will close the tray if it's already been ejected. A handy tool I figured I'd point out :)

---

### Post by Barriehie on 2008-06-03
Cool, I'm going to alias those two!

Barrie

---

### Post by Prospero2006 on 2008-06-04
Here's how you can eject multiple cd drives at once.

[http://www.youtube.com/watch?v=rts0xK5Uu3M](http://www.youtube.com/watch?v=rts0xK5Uu3M)

---

