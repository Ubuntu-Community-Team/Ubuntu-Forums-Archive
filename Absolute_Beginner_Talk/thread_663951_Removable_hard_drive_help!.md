---
title: "Removable hard drive help!"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by bterrill on 2008-01-10
I have an 80 gb removable hard drive and i formatted about 20 gb as an ext3 partition. When i try to view/write to the 20 gb partition it tell me I'm not the owner/i do not have permission to view its contents nor will it let me change the permissions :(

I'm new-ish to linux so there might be something really simple that i overlooked? If anyone could help me out please and thank you

---

### Post by logos34 on 2008-01-10
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(->bottom)

---

### Post by kyphi on 2008-01-10
If your external drive is an USB connected drive you can use the following commands.

First, become the owner:
```
sudo chown bterril:bterrill -R /media/usbdisk
```
then change permissions if needed:
```
sudo chmod -R 777 /media/usbdisk
```

---

### Post by bterrill on 2008-01-10
Thanks guys, worked perfect!:D

---

