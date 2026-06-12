---
title: "NTFS external usb hard drive problem"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by nerds in parties on 2007-03-17
hello there. I have problem with my external hard drive. it cannot be accesable and the error is: 

"cannot mount volume"

it is external USB, NTFS 250GB.

ubuntu 6.10. 

please help.

PS. my most important files for my work is in that hard drive. caution.

---

### Post by taurus on 2007-03-17
See if you can mount from a terminal with these, assuming it's /dev/sda1.

Applications -> Accessories -> Terminal
```
sudo mount -t ntfs /dev/sda1 /media/usbdrive -o nls=utf8,umask=0222
ls -la /media/usbdrive
```

---

### Post by nerds in parties on 2007-03-17
> **taurus said:**
> See if you can mount from a terminal with these, assuming it's /dev/sda1.

Applications -> Accessories -> Terminal
```
sudo mount -t ntfs /dev/sda1 /media/usbdrive -o nls=utf8,umask=0222
ls -la /media/usbdrive
```
mount: mount point /media/usbdrive does not exist

how can i see what name it is?

---

### Post by eljalill on 2007-03-17
You can see what name it is when you type
sudo fdisk -l /dev/sda
in a terminal, or .../sdb, in case you internal hard drive is also connected serially. Or just check in your partition manager.

But before maybe you could try the same as above, only do
sudo mkdir /media/usbdisk
before?

Does that help?

---

### Post by taurus on 2007-03-17
If you are not sure what device it is, run this command from a terminal.

```
sudo fdisk -l
```

---

### Post by nerds in parties on 2007-03-17
> **taurus said:**
> See if you can mount from a terminal with these, assuming it's /dev/sda1.

Applications -> Accessories -> Terminal
```
sudo mount -t ntfs /dev/sda1 /media/usbdrive -o nls=utf8,umask=0222
ls -la /media/usbdrive
```

its sdc, but I get this: 


mount: mount point /media/usbdrive does not exist

---

### Post by h0ax on 2007-03-17
Did you create the folder /media/usbdrive ?

> sudo mkdir /media/usbdrive 

---

### Post by nerds in parties on 2007-03-18
> **taurus said:**
> See if you can mount from a terminal with these, assuming it's /dev/sda1.

Applications -> Accessories -> Terminal
```
sudo mount -t ntfs /dev/sda1 /media/usbdrive -o nls=utf8,umask=0222
ls -la /media/usbdrive
```

I got this:

mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

