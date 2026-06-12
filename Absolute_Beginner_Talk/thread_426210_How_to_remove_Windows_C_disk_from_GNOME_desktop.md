---
title: "How to remove Windows C disk from GNOME desktop?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-04-28
Hello,

I have dual boot system and Disk C, where I have my windwos appears on my ubuntu Gnome desktop. I think it's enough that I can find it in places>computer when I want, I don't need the shortcut on the desktop. How can I remove it? (from the desktop, not from places>computer)

---

### Post by Drakkor on 2007-04-28
```
gconf-editor
```
apps>nautilus>desktop on the bottom right uncheck "volumes visible".  :)

---

### Post by O-pos on 2007-04-28
Nice trick, thank you :)

---

### Post by O-pos on 2007-04-28
It doesn't seem to be as perfect as I thought: now when I use my usb flash disk, it also hides USB icon. is there any way to hide only disk C and let other disks alone?

---

### Post by Freddy kbh on 2007-04-28
resize icon to very small and hide it behind a panel

---

### Post by gogogo111 on 2007-04-28
He shouldn't have to do that though.

---

### Post by Drakkor on 2007-04-28
Is the USB icon also displayed in "Places" ? If so just make the desktop icons invisible. :)

---

### Post by houstonbofh on 2007-04-28
Short answer is no.  Loose both, see both, or do not mount C at all.

---

### Post by Duck2006 on 2007-04-28
You can unmount your windoze drive and mount it as a different file name, but not under /media.
It will not show up on your desktop but under your filesystem with what name you have named it.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by O-pos on 2007-04-28
Ok. So, Like I see there are lots of suggestions. I'll make the icon small temporarily and hide it behind panel, and next time I'll mount it not under /media.

Thanks guys :)

---

