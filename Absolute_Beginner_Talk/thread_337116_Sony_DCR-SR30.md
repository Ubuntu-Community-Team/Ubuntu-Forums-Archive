---
title: "Sony DCR-SR30"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Iarwain ben-adar on 2007-01-12
Hi there,

Today my brother lend me his Sony camera,
and i am eager to take it with me on my holiday so i am trying to make my Kubuntu recognise it.


Kamera does not list this model and i do not know what model would be suited (except for the right one)


How can i use this camera on my pc?


Iarwain

---

### Post by bodhi.zazen on 2007-01-12
Pulg it in, lets see what you've got.

Use the usb cable, good chance it will auto mount ...

---

### Post by Iarwain ben-adar on 2007-01-12
Thakns for the reply,
but it doesn't auto-mount :?


Iarwain

---

### Post by bodhi.zazen on 2007-01-12
In a terminal:

sudo fdisk -l

I assume your camera is at /dev/sda1, so ....

```
sudo mkdir /media/camera
sudo mount /dev/sda1 /media/camera
sudo chmod 777 /media/camera
```

Now browse to /media/camera in konqueror

---

### Post by jhenager on 2007-03-04
> **bodhi.zazen said:**
> In a terminal:

sudo fdisk -l

I assume your camera is at /dev/sda1, so ....

```
sudo mkdir /media/camera
sudo mount /dev/sda1 /media/camera
sudo chmod 777 /media/camera
```

Now browse to /media/camera in konqueror

Had the same problem with my DV-20, and the above instructions needed to be changed to:
sudo mount /dev/sd**b**1 /media/camera
and then it worked great. Imported photos using fspot. Thanks.

---

