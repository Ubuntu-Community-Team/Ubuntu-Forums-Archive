---
title: "Mounting ISO files?"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-04-05
Hi. What is the easiest way to mount an iso file? 

I found something on ubuntuguide:

sudo mkdir /media/iso
sudo modprobe loop
sudo mount file.iso /media/iso/ -t iso9660 -o loop

and to unmount:

sudo umount /media/iso/

But this info is for Ubuntu 5.04. Will it work on Ubuntu 5.10?

---

### Post by trent dillman on 2006-04-05
Sure will!

Note: You probably won't have to modprobe loop, though.

just 

```

sudo mkdir /mnt/iso
sudo mount -o loop /your/iso/file.iso /mnt/iso

```

---

### Post by zugu on 2006-04-05
Thanks for the help.

---

### Post by trent dillman on 2006-04-05
No problem!

---

