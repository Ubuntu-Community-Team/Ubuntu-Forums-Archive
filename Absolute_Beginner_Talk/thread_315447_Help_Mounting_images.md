---
title: "Help Mounting images"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by Ashtarot on 2006-12-09
Hi, i dont know if im double posting or something, i lloked into the forum for something similar, i found a thread that had some infoabout this, fo far i can mount iso files and i can view video DVD's in MPLAYER, but i have some video DVD iso files and i can only view em opening file by file, no menu, so its a little anoyng to see em, is there any way to use em like a normal DVD???

---

### Post by taurus on 2006-12-09
Applications -> Accessories -> Terminal
```
sudo mkdir /media/iso
sudo mount -t iso9660 -o loop **filename**.iso /media/iso
xine dvd://media/iso
```

---

