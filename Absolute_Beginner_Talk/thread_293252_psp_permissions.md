---
title: "psp permissions"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Fittersman on 2006-11-04
when i plug in my psp it mounts automatically but when i try and copy something over to it it wont allow me to

it gives me this error

Error while copying to "/media/psp".
You do not have the permissions to write to this folder.

how can i change that so i can write to it?

---

### Post by taurus on 2006-11-04
You can do it from a terminal with a "sudo cp" command or run "gksudo nautilus" then...

---

### Post by Fittersman on 2006-11-04
is there anyway i can do it that i can just drag and drop because i copied the folders i want moved but when i go to paste  them the paste option isnt highlighted so i cant paste them

---

### Post by taurus on 2006-11-04
That's what "gksudo nautilus" is for!  Open a terminal, Applications -> Accessories -> Terminal, and type

```
gksudo nautilus
```

---

### Post by Fittersman on 2006-11-04
i did but when i do that command a window pops up but it still wont allow me to write to the psp

---

### Post by taurus on 2006-11-05
What format is your psp anyway?

---

### Post by Fittersman on 2006-11-05
what do you mean by format?

---

### Post by taurus on 2006-11-05
Filesystem!!!  Is it NTFS, VFAT, etc.?

---

### Post by Fittersman on 2006-11-05
lol i have no idea and sorry if im not that smart (Absolute Beginner talk)

---

### Post by taurus on 2006-11-05
Okay, show me the output of this command from a terminal!

```
mount
```

---

### Post by Fittersman on 2006-11-05
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
/dev/hda1 on /media/hda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/hda2 on /media/hda2 type ntfs (rw,nls=utf8,umask=007,gid=46)
tmpfs on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw,mode=0755)
/dev/hdd on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=cleippi)
/dev/sda1 on /media/psp type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

---

### Post by taurus on 2006-11-05
So it's a fat32.  Okay, here is what you can do.  First, unmount it and remount it again with write permission for you so you can copy stuff to it.  Open a terminal and do

```

sudo umount /media/psp  <-- to unmount it
sudo cp /etc/fstab /etc/fstab.bak  <-- make a backup copy
gksudo gedit /etc/fstab  <-- open a editor to edit /etc/fstab

```
Now, add the following line to the end of it and save it...

```

/dev/sda1   /media/psp   vfat   defaults,umask=0000   0   0

```
Then, mount it again with

```

sudo mount -a

```
See if you can copy stuff to /media/psp now...  When you are done copying, please DO NOT remove it without unmount it first.

```

sudo umount /media/psp

```

---

### Post by Fittersman on 2006-11-05
cleippi@FamilyComputer:~$ gksudo gedit /etc/fstab

(gedit:22430): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


even though it says that it lets me edit the file but the problem is still the same after i complete your instructions

---

### Post by taurus on 2006-11-05
That is just a warning so don't worry about it with gedit.

You still can't write to your psp!!!

---

### Post by Fittersman on 2006-11-05
Nope!!!](*,)

---

### Post by taurus on 2006-11-05
Is there a writable option/tab on that psp?

---

### Post by Fittersman on 2006-11-05
already checked the box

---

