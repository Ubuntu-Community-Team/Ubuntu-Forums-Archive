---
title: "virtual floppy drive"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by om1 on 2007-10-08
i would like a virtual floppy drive so i can mount floppy images and use it with virtual machines

anyone know of a app?

---

### Post by milosz.galazka on 2007-10-09
Are you searching for functionality provided by *losetup* command?

assign image to device loop0...
```
sudo losetup /dev/loop0 /x/y/floppy.img
```

mount it (maybe you will need to specify -t parameter with filesystem type)
```
sudo mount /dev/loop0 /dir
```

umount
```
sudo umount /dir
```

or just put /dev/loop0 as floppy drive in software you are using

clean up everything
```
sudo losetup -d /dev/loop0
```

---

