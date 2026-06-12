---
title: "Read/write Ubuntu partition from Ubuntu live cd? [Resolved]"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by miggols99 on 2007-04-07
Can someone tell me how to access files in a Ubuntu partition from a Ubuntu 6.06 live cd? I want to restore my old xorg.conf file. Lucky I submitted it to these forums ;)

---

### Post by xopher on 2007-04-07
```
sudo mkdir /media/ubuntu; sudo mount /dev/hda1 /media/ubuntu
```

If your installed ubuntu is on /dev/hda1, then use the exact cmd ^ - otherwise edit it approptiately. You can then browse /media/ubuntu with eg. nautilus.

---

### Post by aysiu on 2007-04-07
If you want to be able to make changes after following xopher's advice, you should press Alt-F2 and type ```
gksudo nautilus
```

---

### Post by miggols99 on 2007-04-07
Ok, thanks. I've got it working now.

---

