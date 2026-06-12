---
title: "Getting some error message running gk sudo nautilus"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2006-09-06
I needed to run gksudo nautilus (to flash firmware on my iRiver DAP) and I think it worked but, when I ran it, I got this : > (nautilus:31304): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:31304): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

(nautilus:31304): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

(nautilus:31304): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

(nautilus:31304): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

(nautilus:31304): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

(nautilus:31304): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

(nautilus:31304): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

(nautilus:31304): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

(nautilus:31304): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

(nautilus:31304): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)


Yes, it just kept repeating the same line, guess looking for the file/directory ? Anyway, Nautilus did come up, and I managed to move the files needed, but I'm just wondering what is up with that up there ?

Doug

---

### Post by croak77 on 2006-09-07
Do you have /usr/lib/gnome-vfs-2.0/modules/libcdda.so on your system? If not try installing libgnome-vfs-common. Or maybe try sudo dpkg-reconfigure libgnome-vfs-common.

---

### Post by Sweet Spot on 2006-09-07
Thanks Croak.  I had to install "libgnome-vfs-common". Any reason this isn't installed automatically ?

---

