---
title: "delete old folders in /media directory"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Balinsky on 2007-05-04
Ok in my /media directory there are many old unused folders

for example there is a /media/ipod

i cant $ sudo rm ipod
it tells me
rm: cannot remove `/ipod': No such file or directory

itd be awesome if i could remove some old external hard drive folders so i could bet my settings back

thanks 
jebsky

---

### Post by taurus on 2007-05-04
```
sudo rmdir /media/ipod
```
or
```
cd /media
sudo rmdir ipod
```

---

### Post by aysiu on 2007-05-04
Try Alt-F2 ```
gksudo nautilus
``` Control-L ```
/media
```

---

### Post by Balinsky on 2007-05-04
thanks both of u

aysiu that truck to run nautilus as a super user is neat. 

while i am on the topic of permissions i have a fat32 partition mounted with fstab at /media/Docs

the fstab line is 
```
/dev/sda5               /media/Docs      vfat         defaults                    0  0  
```

when i run nautilus as su i can manipulate files otherwise i cannot

any help would be awesome

thanks again 

Jebsky

---

### Post by taurus on 2007-05-04
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and change the current entry for /dev/sda5 to look like this then.

```
/dev/sda5   /media/Docs   vfat   iocharset=utf8,umask=000   0   0
```
Save it and reboot.

---

