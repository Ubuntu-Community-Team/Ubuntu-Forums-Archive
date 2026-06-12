---
title: "floppy mount problems"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by cayamara on 2006-03-18
I know there are many threads about that out there, but they did't help.

The relevant part of the /etc/fstab:
```
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

This is what I tried:
```
$ mount /media/floppy0
mount: Device /dev/fd0 doesn't exist
$ sudo mount -t vfat /dev/fd0 /media/floppy0
mount: Device /dev/fd0 doesn't exist
$ ls /dev/|grep 'fd'
fd
$ ls /dev/fd*
0  1  2  3
```

So basically I don't seem to have a /dev/fd0. Why? :confused: I'm kinda lost, and I didn't have trouble before with mounting stuff (like my iPod).

Hoping for help ...

---

### Post by Pragmatist on 2006-03-18
What kind of floppy drive?
Please give output of these commands: NOTE: Type these exactly as I've given them. I didn't misspell anything. **loppy** is what I want
```
ls -l /dev/fd0
```
```
ls -l /media
```
```
dmesg | grep loppy
```
```
dmesg | grep fd0
```
```
cat /var/log/messages | grep loppy
```
```
cat /var/log/messages | grep fd0
```
```
lshal | grep loppy
```
```
lshal | grep fd0
```

btw, nice reference to "Cat's Cradle" by Vonnegut :)

---

### Post by cayamara on 2006-03-18
[QUOTE=Pragmatist]Please give output of these commands:[/QUOTE]
Ok, here it goes. Looking at the output, I think that my floppy drive is broken. The light of the drive is on though so it is at least connected to the power.
```

$ ls -l /dev/fd0
ls: /dev/fd0: Datei oder Verzeichnis nicht gefunden
*(ls: /dev/fd0: file or directory not found)*

$ ls -l /media
insgesamt 18
*(total of 18)*
lrwxrwxrwx 1 root root    6 2006-01-14 15:28 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2006-01-14 15:28 cdrom0
dr-xr-xr-x 1 root root 2048 2006-03-18 12:14 cdrom1
lrwxrwxrwx 1 root root    7 2006-01-14 15:28 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2006-01-14 15:28 floppy0
drwxr-xr-x 2 root root 4096 2006-02-12 15:57 ipod
drwxrwxrwx 7 root root 4096 1970-01-01 01:00 windows

$ dmesg | grep loppy
*(no output)*

$ dmesg | grep fd0
*(no output)*

$ cat /var/log/messages | grep fd0
*(no output)*

$ cat /var/log/messages | grep fd0
*(no output)*

$ cat /var/log/messages | grep loppy
*(no output)*

$ lshal | grep loppy
*(no output)*

$ lshal | grep fd0
*(no output)*
```
[QUOTE=Pragmatist]btw, nice reference to "Cat's Cradle" by Vonnegut :)[/QUOTE]Thanks ;)

---

### Post by Pragmatist on 2006-03-18
Well, Linux definitely doesn't think you have a floppy drive.  
> The light of the drive is on though so it is at least connected to the power.
On most floppy drives I've used, the light only goes on when the drive is accessing a floppy.

Maybe your drive is broken, since Linux virtually always recognizes floppy drives.  It is possible that the drive's cable to the motherboard is loose.  Is it an IDE floppy drive?  An internal USB floppy drive?

---

### Post by mlind on 2006-03-18
```

sudo modprobe floppy

```

current PnP system is somewhat broken on on Dapper atleast.
you need to modprobe floppy separately.

---

### Post by cayamara on 2006-03-18
[QUOTE=mlind]```

sudo modprobe floppy

```

current PnP system is somewhat broken on on Dapper atleast.
you need to modprobe floppy separately.[/QUOTE]
Wow, thanks, I would have never thought of that. It works. Thanks to you too, Pragmatist.

---

### Post by mlind on 2006-03-18
[QUOTE=cayamara]Wow, thanks, I would have never thought of that. It works. Thanks to you too, Pragmatist.[/QUOTE]

Glad you got it sorted.

You can add *floppy* in /etc/modules to get this working without a modprobe

---

