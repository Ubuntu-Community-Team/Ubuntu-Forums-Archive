---
title: "Converting *.img to *.iso"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by Klejs on 2006-03-12
Hi, 

I would like to know if there is any way I can convert an *.img file to an
*.iso?

---

### Post by kaamos on 2006-03-12
I think the files are just about the same. You can mount and .img like this
```
sudo mkdir /media/temp
sudo mount /path/to/file.img /media/temp
```
Or you can burn it to disk just like an iso.

---

### Post by Klejs on 2006-03-12
The problem was that gnomebaker doesnt have the support to burn an .img file as an disc image...

But I'll try the mounting and see what I can do...ty!

---

### Post by patrick295767 on 2006-03-12
[QUOTE=Klejs]The problem was that gnomebaker doesnt have the support to burn an .img file as an disc image...

But I'll try the mounting and see what I can do...ty![/QUOTE]
  
For Converting cd /dvd , I use wine with: 
   
winimage   (wine)
winiso    (wine)
  
==
Hope it can help

---

### Post by knalle on 2006-03-12
think it can be done without wine too, what kind of img file is it, and where did you get it from?

---

### Post by patrick295767 on 2006-03-12
Ahhh,

Additional information, for mounting to mountpoint my cd images, exotic for linux, like after clonecd with cue file , I used :
  cdemu-0.7   
(and also kcdemu_0.4.0 )
  
(to mount an iso file: mount -o loop -t iso9660 filename.iso /mnt/iso)

Greetz

---

### Post by Klejs on 2006-03-12
I solved it, mounted the img file as /cdrom

Used gnomebaker to make an iso of the /cdrom dir

Burned an disc image in gnomebaker of the iso image.

---

### Post by Klejs on 2006-03-12
If you want to make an ISO file out of an disc you can use the **dd** command:

```
dd if=/dev/device of=/path/to/iso/file.iso
```

Works great for both DVD's and CD's

---

