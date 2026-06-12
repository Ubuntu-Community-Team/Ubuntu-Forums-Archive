---
title: "Iso mounting help"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by BlahMan_of.Doom on 2007-06-14
I'm trying to mount an iso using
```
sudo mount file.iso /media/iso/ -t iso9660 -o loop
```
But it gives me this error:
```
mount: Not a directory
```
I have already created a /media/iso directory, and I don't know what else could be wrong. Please help!

---

### Post by schorsch on 2007-06-14
> **BlahMan_of.Doom said:**
> I'm trying to mount an iso using
```
sudo mount file.iso /media/iso/ -t iso9660 -o loop
```
But it gives me this error:
```
mount: Not a directory
```
I have already created a /media/iso directory, and I don't know what else could be wrong. Please help!

Try 

```
mount -t iso9660 -o loop file.iso /media/iso
```

---

### Post by BlahMan_of.Doom on 2007-06-14
Same error. I tried it in sudo and su.

EDIT: Does the iso have to be in / ?

---

### Post by schorsch on 2007-06-14
> **BlahMan_of.Doom said:**
> Same error. I tried it in sudo and su.

EDIT: Does the iso have to be in / ?

No, the iso can be somewhere in your filesystem. 

So, please try this sequence of commands:

```
cd *directory_with_file.iso*
sudo mkdir /media/iso
sudo mount -t iso9660 -o loop ./file.iso /media/iso
```

---

### Post by BlahMan_of.Doom on 2007-06-14
Doesn't work. Same error.

---

### Post by earobinson on 2007-06-14
could you cut and paste exactly what happens in the terminal?

---

### Post by schorsch on 2007-06-14
Could you please send the following output:

```
cd /media
ls -la

```

---

### Post by BlahMan_of.Doom on 2007-06-14
> **earobinson said:**
> could you cut and paste exactly what happens in the terminal?
The output is in the first post. Here it is again:
```
mount: Not a directory
```
> **schorsch said:**
> Could you please send the following output:

```
cd /media
ls -la

```
Here you go:
```
CENSORED@desktop:/media$ ls -la
total 20
drwxr-xr-x  5 root root    4096 2007-06-14 11:13 .
drwxr-xr-x 23 root root    4096 2007-06-14 10:03 ..
lrwxrwxrwx  1 root root       6 2007-06-14 01:59 cdrom -> cdrom0
drwxr-xr-x  2 root root    4096 2007-06-14 01:59 cdrom0
-r-Sr-----  1 root root       0 2007-04-15 05:03 .hal-mtab-lock
drwxr-xr-x  2 root root    4096 2007-06-14 10:34 iso
dr-xr-x---  1 root plugdev 4096 2007-06-13 23:42 sda1

```

---

### Post by schorsch on 2007-06-14
weird ... could it be that the iso-image is corrupted? How did you create this one or was it just copied from somewhere else?

---

### Post by BlahMan_of.Doom on 2007-06-14
I had to use mdf2iso to make the iso..I mean, Can anyone help me mount an mds so there's no chance of corruption?

---

### Post by schorsch on 2007-06-14
Uhm, sorry i never used this tool before. But if you take a look at the homepage

[http://mdf2iso.berlios.de/]("http://mdf2iso.berlios.de/")

there seems to be a tool named IAT to analyze the image.

---

### Post by BlahMan_of.Doom on 2007-06-14
It says there is something wrong..so can someone tell me how to mount an mdf using FuseISO?

---

### Post by Vil on 2007-08-20
Try installing AcetoneISO2 Pro 
Here's a guide to it... 
[http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html](http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html)

---

