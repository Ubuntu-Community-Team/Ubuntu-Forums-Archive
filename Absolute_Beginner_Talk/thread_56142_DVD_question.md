---
title: "DVD question"
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by Watcher on 2005-08-11
So I tried to play a dvd today, installed everything on the ubuntu guide said I had to do, loaded up xine, started it, put in my dvd, everything works but one thing.

When looking at the screen it sort of stutters somethings, not much, very little, but just a bit too much to not be irritating, so I looked around a bit here found out that I had to enable DMA on my cd drive, but I always get this error:

bernard@bernardtux:~$ sudo hdparm -d1 /dev/cdrom

> /dev/cdrom:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

Any ideas? I get the same error when trying  /dev/dvd

---

### Post by Stormy Eyes on 2005-08-11
Try **sudo modprobe ide-dma** and **sudo modprobe ide-cd** to see if you need the kernel's DMA driver for IDE drives installed, and then use hdparm again. If that works, then do **sudo gedit /etc/modules.conf** and add "ide-dma" and "ide-cd" to the list. Is your main hard drive a SATA drive, by any chance? I had a similar problem.

---

### Post by Watcher on 2005-08-11
[QUOTE=Stormy Eyes]Try **sudo modprobe ide-dma** and **sudo modprobe ide-cd** to see if you need the kernel's DMA driver for IDE drives installed, and then use hdparm again. If that works, then do **sudo gedit /etc/modules.conf** and add "ide-dma" and "ide-cd" to the list. Is your main hard drive a SATA drive, by any chance? I had a similar problem.[/QUOTE]
yes it is a sata drive

after doing those sudo's i get this, so how do i get the ide-dma (i think need that one?)
> 
bernard@bernardtux:~$ sudo modprobe ide-dma
FATAL: Module ide_dma not found.
bernard@bernardtux:~$ sudo modprobe ide-cd
bernard@bernardtux:~$

---

### Post by Stormy Eyes on 2005-08-11
OK. Try doing the following, rebooting, and doing hdparm again. If your computer acts wierd, you can always move /etc/modules.original back to /etc/modules.

```
sudo cp /etc/modules /etc/modules.original
sudo wget ubuntupc.com/ubuntu/new_etc_modules -O /etc/modules
sudo cp /etc/hdparm.conf /etc/hdparm.conf.original
sudo wget ubuntupc.com/ubuntu/new_hdparm.conf -O /etc/hdparm.conf
```

---

