---
title: "gparted problems"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by stubblepoo on 2008-02-02
i have installed gparted and although it shows up in add/remove programs program i cannot access it through any menu's nor it seems anything else i have tried to install.
any help mucho apreiciated

---

### Post by mikeyphi on 2008-02-02
> **stubblepoo said:**
> i have installed gparted and although it shows up in add/remove programs program i cannot access it through any menu's nor it seems anything else i have tried to install.
any help mucho apreiciated

Open Synaptic - search for gparted. When found - it should have a green box if it's installed (if not-install)
When installed the icon should be found under System/Administration as Partition Editor

---

### Post by jan quark on 2008-02-02
in terminal

```
sudo gparted
```

---

### Post by UltraMathMan on 2008-02-02
Gparted is normally found under System->Administration->Partition Editor. Alternatively you can open a terminal and type ```
sudo gparted
``` to start it. Note that you cannot make changes to a partition you have mounted, so if you want to make changes to you root partition for instance, you would need to do so from a live cd.

-Hope this helps :)

---

### Post by dstew on 2008-02-02
Actually, I think```
gksudo gparted
```is the proper command.

---

### Post by bruce89 on 2008-02-02
You can't do anything with GParted when the partitions are mounted (which they are likely to be), so I suggest using the official [GParted LiveCD]("http://gparted-livecd.tuxfamily.org/").

---

