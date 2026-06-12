---
title: "unmounting ?!?!?!?"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by djlilyazi on 2006-01-09
ok i mount my windows harddrive..
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)
following this site..

how do i unmount them i did what that site said they are still on my desktop and on the media folder and i can still access them...how do i unmount permentaly ?

thanks,

YAZ

---

### Post by Omnios on 2006-01-09
Umount in terminal will unmount  them. If you made an entry  in fstab you have to remove or comment out "#" what you added with #. Commenting out allows you to uncomment later if you wish to automaout again otherwwise it ignores it if commented out.

 sudo gedit /etc/fstab

 Undo  your changes or if you made aa backup of fstab you can simply

 sudo cp /etc/fstab_backup /etc/fstab

---

### Post by djlilyazi on 2006-01-09
[QUOTE=Omnios]Umount in terminal will unmount  them. If you made an entry  in fstab you have to remove or comment out "#" what you added with #. Commenting out allows you to uncomment later if you wish to automaout again otherwwise it ignores it if commented out.

 sudo gedit /etc/fstab

 Undo  your changes or if you made aa backup of fstab you can simply

 sudo cp /etc/fstab_backup /etc/fstab[/QUOTE]

i did what u said the gedit did not come up but ya i had a back up and i did that ... so how do i check if its gone forever since it is auto when i start my linux everytime ?..

and my root is acting up how do i check if i am the owner of everything here...

---

### Post by patrick295767 on 2006-01-11
```
sudo apt-get -f -y install rox-filer
```
this prog 
```
xterm
rox &
```
  
is very handy to unmount the /mnt/folders
 it's asking you to un-/mount them from the /etc/fstab
  
-----------------
if troubles with unmounting
ALT-F1
you can try the forced un-mounting
or also the lazy one !
  (man mount)

---------------------
Greetz'

---

### Post by djlilyazi on 2006-01-11
kool...thanks it worked...

---

