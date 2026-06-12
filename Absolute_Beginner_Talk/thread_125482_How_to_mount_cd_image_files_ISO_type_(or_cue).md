---
title: "How to mount cd image files ISO type (or cue) ?"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-02-04
How to mount cd image files ISO type (or cue) ?
```

mount -t   something ???
```

Thank you !

Patrick

---

### Post by tehwa on 2006-02-04
The starter guide reminds me:

[http://doc.ubuntu.com/ubuntu/desktopguide/C/ch04.html#id2589750](http://doc.ubuntu.com/ubuntu/desktopguide/C/ch04.html#id2589750)

> 
To mount Image (ISO) file

```
sudo mkdir /media/iso
sudo modprobe loop 
sudo mount file.iso /media/iso/ -t iso9660 -o loop
```

To unmount Image (ISO) file

```
sudo umount /media/iso/
```


---

### Post by tehwa on 2006-02-04
Woops, double posted.

---

### Post by patrick295767 on 2006-02-04
Merci !!

---

### Post by patrick295767 on 2006-02-04
I noticed just now that this is not workign cos I made the image of the cd with clonecd .. 
If you would known eventually how to mount ccd or cue or sub images of cd, plz do not hesitate to let me know .

 Thank yiou again !

Patrick

---

### Post by patrick295767 on 2006-02-04
I found a very nice link :

[http://linuxreviews.org/howtos/cdrecording/]("http://linuxreviews.org/howtos/cdrecording/")

---

### Post by MetalMusicAddict on 2006-02-04
You might find [THIS]("http://www.ubuntuforums.org/showthread.php?t=87369") interesting.

---

### Post by patrick295767 on 2006-02-04
To mount cue: 
 ==========
  
You download the cdemu 
```
make
make install 
modprobe cdemu
```
  
Then :
$ cdemu 0 image.cue
$ mount /dev/cdemu/0 /mnt/cdrom

Enjoy !!

---

### Post by patrick295767 on 2006-02-04
you should also maybe be root depending of ur config:
then
  
type:
```
mount -t iso9660 /dev/cdemu/0 /mnt/iso
```
  
U can then read the clone cd files.
  
Greetings

---

### Post by dustman on 2008-01-27
if anyone is subscribed to this thread, i guess GMountISO is a great tool : [http://phorolinux.com/mount-iso-image-file-iso-with-gmount-iso.html](http://phorolinux.com/mount-iso-image-file-iso-with-gmount-iso.html) . You could install it from a terminal too: ```
sudo apt-get install gmountiso
``` Then go to Applications->System Tools->Gmount-iso.

---

### Post by Shadowmeph on 2008-02-17
> **patrick295767 said:**
> To mount cue: 
 ==========
  
You download the cdemu 
```
make
make install 
modprobe cdemu
```
  
Then :
$ cdemu 0 image.cue
$ mount /dev/cdemu/0 /mnt/cdrom

Enjoy !!

ok I am a noob how do I load cdemu and where do I put those commands

---

