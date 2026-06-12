---
title: "HDD in Ubuntu"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by kubo158 on 2006-03-26
i have problem !!!! i mounted my 4 gb HDD to ubuntu but i can't write any files to this disk, it's FAT32 on hdd, where is the problem please help

---

### Post by astyanax on 2006-03-26
To mount a FAT 32 partition with Read/Write permissions, do this:
```
sudo mount /dev/hdd# /media/windows/ -t vfat -o iocharset=utf8,umask=000

```

To unmount:
```
sudo umount /media/windows/

```

To mount at boot:
```
sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

```

Append this line to the fstab:
```
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

```

All of this information was obtained from the Ubuntu Guide at [http://www.ubuntuguide.org](http://www.ubuntuguide.org).  The guide is pretty straight forward and helped me out with alot of basic questions when I was first starting out with Ubuntu

[URL="http://www.ubuntuguide.org/#mountunmountfat"]Specific Link
[/URL]

---

### Post by cisde on 2006-03-28
I think you'll also need
sudo mkdir /media/windows
before you try to mount it manually the first time.
David

---

