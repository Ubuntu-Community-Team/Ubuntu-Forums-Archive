---
title: "OS 8 commercial tutorial CD's"
date: 2011-09-27
forum: Any Other OS
---

### Post by casbahdk on 2011-09-27
I have some commercial, tutorial CD's that I would like to access on my current desktop running Xubuntu 11.04. The tutorials are made with an early version of QuickTime and I remember using them under OS 8, but I can't get the CD's to mount either in Xubuntu or Win XP.

Can anyone advise me as to how to mount and play the CD's?

---

### Post by casbahdk on 2011-10-02
The answer is as follows:
```
sudo apt-get install hfsutils hfsplus
```
```
sudo mount -t hfs /dev/sr0 /cdrom
```

---

### Post by sffvba[e0rt on 2011-10-02
Wow, wouldn't have thought they used that file-system on CD's too.


404

---

### Post by casbahdk on 2011-10-03
Yeah, it was a real surprise for me too.

---

