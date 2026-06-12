---
title: "accessing hard drive from live CD"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by rcdawson on 2006-11-19
Booting from live CD, ubunto puts my hard drive in /tmp/disks-hda1, but says I haven't the permissions to read it.(I have abreviated the name of the mount point).    It shows up in the gui administrative Disks tool as being accessible.  I opened a terminal, did "sudo chmod go+rwx, and it said it was changing permissions.  None the less, I stall cannot access it.

I tried mounting it somewhere else, but that wasn't allowed.

Any ideas?

---

### Post by redbluemangle on 2006-11-19
I am assuming you're trying to access your root (/) partition. If that is the case check out this guide.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by aysiu on 2006-11-19
Press Alt-F2 to get a run dialogue.

If you're using Ubuntu, type ```
gksudo nautilus
``` If you're using Kubuntu, type ```
kdesu konqueror
``` and if you're using Xubuntu, type ```
gksudo thunar
```

---

