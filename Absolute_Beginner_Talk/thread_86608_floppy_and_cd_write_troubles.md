---
title: "floppy and cd write troubles"
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by generalstoner on 2005-11-05
I cannont write to or erase a floppy or cd, It says I dont have pemession. I cant figure out how to fix this does anyone know how.

---

### Post by adwait on 2005-11-05
Try starting your floppy/ writing / cd burning programs from a terminal and prefixing sudo to it. eg if you use k3b for burning cds:
```
sudo k3b
```/

For a long term solution, open the fstab file
```
sudo gedit /etc/fstab
```
*ERROR CORRECTED

find the coresponding lines for your floppy/cd, usual something like /dev/fd0 for your floppy.

Add the word user to it: eg
> /dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdb        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by generalstoner on 2005-11-05
when I tried to edit the bat I got this message
>  GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.


---

### Post by Mustard on 2005-11-05
The command above has a typo in it.  The actual command is

```
sudo gedit /etc/fstab
```

Even given that the command has a typo in it, your error seems to be related to something else.

-edit-

I just tried running the command above, using gksudo, and that seems to replicate you error.

```
seablue@radagast:/etc$ gksudo gedit /etc/fstab

(gedit:10952): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

Are you typing gksudo instead of sudo?

---

### Post by generalstoner on 2005-11-05
I just copy/pasted and I got that error

I got it to open but the user was already in there and I still cant erase/write to my floppy or cd... my floppy is what I really need right now though

---

### Post by Mustard on 2005-11-05
after changing the entries you need to unmount the drives with a umount command and then remount them again.  Ideally running mount -a should work, but in practice mount -a only works if the drives are umounted first.

```
man mount #manual for the mount command

man umount #manual for the umount command
```

---

### Post by generalstoner on 2005-11-05
when I go to mount them I get this error now...
> Error: given UDI is not a mountable volume


---

### Post by Kapre on 2005-11-05
[QUOTE=generalstoner]when I go to mount them I get this error now...[/QUOTE]

general - this is a bug in Breezy and it has already been reported. For a workaround (so you can mount it) on it, please see this [thread]("http://www.ubuntuforums.org/showthread.php?t=78986&highlight=floppy+mounting").

K

---

### Post by generalstoner on 2005-11-05
thanks for the help, I love the cumminity here. Everything is working fine.

---

### Post by Mustard on 2005-11-06
[QUOTE=Kapre]general - this is a bug in Breezy and it has already been reported. For a workaround (so you can mount it) on it, please see this [thread]("http://www.ubuntuforums.org/showthread.php?t=78986&highlight=floppy+mounting").

K[/QUOTE]

Hmmm..interesting.  Goes to show how often I use my floppy drive. I'd never noticed that.

---

