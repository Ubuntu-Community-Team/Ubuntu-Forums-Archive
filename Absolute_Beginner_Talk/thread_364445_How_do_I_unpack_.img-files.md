---
title: "How do I unpack .img-files?"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by robbma on 2007-02-18
Hi, is there any program to unpack .img-files in Ubuntu and how to use it?

---

### Post by highneko on 2007-02-18
Applications > Accessories > Terminal
[COLOR="Gray"]# Then make a directory where you want the file mounted:[/COLOR]
sudo mkdir /image
[COLOR="Gray"]# Then mount the image on the directory:[/COLOR]
sudo mount -o loop /path/to/file.img /image
[COLOR="Gray"]# Then you could open the directory with nautilus:[/COLOR]
nautilus /image

---

### Post by robbma on 2007-02-18
> **highneko said:**
> Applications > Accessories > Terminal
[COLOR="Gray"]# Then make a directory where you want the file mounted:[/COLOR]
sudo mkdir /image
[COLOR="Gray"]# Then mount the image on the directory:[/COLOR]
sudo mount -o loop /path/to/file.img /image
[COLOR="Gray"]# Then you could open the directory with nautilus:[/COLOR]
nautilus /image

Ok then how do I unmount the file?

---

### Post by highneko on 2007-02-18
# Should be something like this:
sudo umount /image

---

### Post by robbma on 2007-02-18
Ok thanks for the answers

---

