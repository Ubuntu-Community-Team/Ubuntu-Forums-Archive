---
title: "help ntfs mounting permission problem......... tired"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Maccabee on 2008-02-10
hi 
i ve an ntfs drive n in linux i ve edited the fstab.it mounts perfectly well..i can see the icon on desktop
but nw the frustrating part comes whenever i double click it to open it tells me you dont hav the sufficient permissions to view the contents of this folder

i open it as root frm terminal #nautilus /media/hda1 then no problem
but ive to use the terminal each time this is very annoying
can anyone provide me a solution
thanks

---

### Post by linuxisfree on 2008-02-10
> **Maccabee said:**
> hi 
i ve an ntfs drive n in linux i ve edited the fstab.it mounts perfectly well..i can see the icon on desktop
but nw the frustrating part comes whenever i double click it to open it tells me you dont hav the sufficient permissions to view the contents of this folder

i open it as root frm terminal #nautilus /media/hda1 then no problem
but ive to use the terminal each time this is very annoying
can anyone provide me a solution
thanks


Try this:
```
sudo chmod 0777 /media/hda1
```

---

### Post by dynamethod on 2008-02-10
you sure you got your fstab setup correct? post your cat /etc/fstab

---

### Post by vanadium on 2008-02-10
@dynamethod: This is the absolute beginners forum, so probably you should be more explicit with your instructions.

* Open a command terminal (Applications - Accessories - Terminal)
* type the command

cat /etc/fstab

* Select all output you obtain, copy it to the clipboard and paste it in your reply here.

Indeed, the best approach is to specify the user in fstab, although the approach of changing the permissions of the mount point (suggestion of linuxisfree) probably also works (provided presumably it doe not conflict with specifications in fstab)

---

### Post by jan quark on 2008-02-10
first make sure you have ntfs3g installed
```
sudo apt-get install ntfs-3g
```

now to find the correct name of the ntfs partition run this

```
sudo fdisk -l | grep NTFS
```


when you have the name we have to configure the fstab file

we first create a backup 
```

sudo cp /etc/fstab /etc/fstab.bak
```

and then access the file with
```
gksu gedit /etc/fstab
```


either you ntfs is already there than change the line to this

```
/dev/<your partition>     /media/<mount point>     ntfs-3g     defaults,locale=en_US.utf8   0    0
```
your partition is of course the name of your partition
and mount point the real mount point like for instance /media/data

if it is not there you have to create a new mount point first with

```
sudo mkdir /media/<the name you want>
```

finally remount your ntfs partition
```

sudo umount /dev/<your partition>
sudo mount -a
```

---

