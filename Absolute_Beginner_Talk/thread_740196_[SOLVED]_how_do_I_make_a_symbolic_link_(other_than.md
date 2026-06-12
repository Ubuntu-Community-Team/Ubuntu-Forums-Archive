---
title: "[SOLVED] how do I make a symbolic link (other than by marrying)?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by lila on 2008-03-30
Hello,
I'm trying to install gxine.  But it won't recognise the DVD drive.  The configuration assistant tells me:

could not access dvdrom: /dev/dvd
Either create a symbolic link /dev/dvd pointing to your cdrom device or set your cdrom device in the preferences dialogue

I looked into the preferences dialogue and can't find the cdrom device at all (although it does work), but can find the dvd drive which was set to be read automatically by totem.  I changed that to gxine but that doesn't seem to help.

My understanding of these terms seems inadequate:
A "symbolic link" is a marriage between two people.
"Pointing to the dvd device" I would do that with my index finger...

What do I do?  Can someone translate?:lolflag:

Thanks for any help!
Lila

---

### Post by Michael.Godawski on 2008-03-30
run in terminal

```
ln -s /path/to/real/file /path/to/non-existant/file
```
[http://www.beginlinux.org/mod/resource/view.php?id=916](http://www.beginlinux.org/mod/resource/view.php?id=916)

> Creating a Symbolic Link to a File or Folder

A symbolic link is a special type of file that points to another file or folder. When you perform an action on a symbolic link, the action is performed on the file or folder to which the symbolic link points. However, when you delete a symbolic link, you delete the link file, not the file to which the symbolic link points.

To create a symbolic link to a file or folder, select the file or folder to which you want to create a link. Choose Edit &#8594; Make Link. A link to the file or folder is added to the current folder.

Alternatively, grab the item to which you want to create a link, then press-and-hold Ctrl+Shift. Drag the item to the location where you want to place the link.

By default, the file manager adds an emblem to symbolic links.
from [https://help.ubuntu.com/7.10/user-guide/C/gosnautilus-8.html](https://help.ubuntu.com/7.10/user-guide/C/gosnautilus-8.html)

---

### Post by lila on 2008-03-30
Hi,
thanks, but I'm afraid I don't get it.
I tried the terminal command, it came up with: 

ln: création d'un lien symbolique `/path/to/non-existant/file' vers `/path/to/real/file': Aucun fichier ou répertoire de ce type

Sorry, that's in French, it says: ln: creation of a symbolic link `/path/to/non-existant/file' to `/path/to/real/file': no such file or directory.

And the guide text... well, but how do I know which is the file or folder that I want to create a link to, or indeed where it is located?

Lila

---

### Post by annda on 2008-03-30
hi,

you should use the actual filenames of the devices (because devices are represented by files in Linux), like this:

```
sudo ln -s /dev/cdrom /dev/dvd
```

the sudo command is necessary - it tells the system that you are acting as root (administrator) and you are allowed to change system settings and files

p.s. if the sommand succeeds but gxine still complains, try cdrom0 instead of cdrom

---

### Post by lila on 2008-03-30
Thanks a lot,
that did it!  I'll see if I can read a DVD now...
Lila

---

