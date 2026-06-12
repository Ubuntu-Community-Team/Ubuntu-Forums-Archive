---
title: "My floppy wont mount..."
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by keithbraafladt on 2006-01-25
How do I set ubuntu to allow me to mount the floppy? when I try to open it it says that I don't have root permission, and I'd like it to be mountable for any user.
Thanks

---

### Post by localzuk on 2006-01-25
Open a terminal and type ```
sudo gedit /etc/fstab
```

Look for a line with /dev/fd0 in and find the it should resemble the following:

```

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by keithbraafladt on 2006-01-26
okay I'm looking at the line... what do I change it to? ( your example doesn't seem to  have a change in it)
Thanks

---

### Post by keithbraafladt on 2006-01-26
[QUOTE=keithbraafladt]okay I'm looking at the line... what do I change it to? ( your example doesn't seem to  have a change in it)
Thanks[/QUOTE]
oh here is the line
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by ubunlilluz on 2006-01-26
try to change auto with vfat.
In another 3d has been discussed about a bug of ubuntu and a package to fix it. Try to search it.

---

### Post by keithbraafladt on 2006-01-26
[QUOTE=ubunlilluz]try to change auto with vfat.
In another 3d has been discussed about a bug of ubuntu and a package to fix it. Try to search it.[/QUOTE]

Okay as a newbie I just want to be clear: you mean change the "auto" in the floppy line to "vfat" or is "vfat some linux terminal command?
Thanks for you patience
k.

---

### Post by markd on 2006-01-26
Yes, ubunlilluz meant change "auto" to "vfat" (which is a filesystem type).  But I don't know if that's the problem.  The "user" in that line should mean that any user can mount the device.  How are you trying to mount it? Using the command "mount /dev/fd0" should do it.  If you give the full mount command "mount -t vfat /dev/fd0 /media/floppy0" it will say that you must be root, but giving the abbreviated form should make it look in /etc/fstab and see that any user can mount it.  HTH.

---

