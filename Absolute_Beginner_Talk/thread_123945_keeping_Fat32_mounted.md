---
title: "keeping Fat32 mounted"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-01-31
I have mounted my Fat32 partition but on each reboot the icon (HDA7) in this case is not there. This is what I have done ' sudo mkdir /media/hda7'
'sudo mount /dev/hda7 /media/hda7 -t vfat -o umask=000' The icon is placed on the desktop but does not stay there on reboot. What is it I am missing? Thanks

---

### Post by lha on 2006-01-31
[QUOTE=Sbarton]I have mounted my Fat32 partition but on each reboot the icon (HDA7) in this case is not there. This is what I have done ' sudo mkdir /media/hda7'
'sudo mount /dev/hda7 /media/hda7 -t vfat -o umask=000' The icon is placed on the desktop but does not stay there on reboot. What is it I am missing? Thanks[/QUOTE]

Open terminal (Applications->Accessories->Terminal) and type
```
sudo gedit /etc/fstab
```
In the end of that file, add
```
/dev/hda7       /media/hda7     vfat    umask=000         0       0
```
Hda7 will be mounted next time you boot.

---

### Post by Gcool on 2006-01-31
You need to add it to /etc/fstab:

sudo nano /etc/fstab

and add the following line:

/dev/hda7  /media/hda7  vfat  defaults  0 0

---

### Post by aysiu on 2006-01-31
Iha's got it.

If you do it GCool's way, it'll be mounted so that only root can read it (not users)--that's what *defaults* means.

---

### Post by Gcool on 2006-01-31
[QUOTE=aysiu]Iha's got it.

If you do it GCool's way, it'll be mounted so that only root can read it (not users)--that's what *defaults* means.[/QUOTE]

You're absolutely right. My bad.

---

### Post by Sbarton on 2006-01-31
[QUOTE=lha]Open terminal (Applications->Accessories->Terminal) and type
```
sudo gedit /etc/fstab
```
In the end of that file, add
```
/dev/hda7       /media/hda7     vfat    umask=000         0       0
```
Hda7 will be mounted next time you boot.[/QUOTE]

Yes! Thats it!  Up and running. Many thanks to you and all those who replied.

---

