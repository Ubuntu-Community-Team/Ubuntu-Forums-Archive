---
title: "Ubuntu Live Permissions"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by ubuntuforhumans on 2006-02-22
Hi,

I have installed ubuntu Live CD (Version 5.04) in order to retrieve files from my crashed windows 2000 machine. However when I try to open my newly created folder it is telling me I do not have permissions to view. Here are the steps I have followed;

Boot machine from Live CD and install.

Open a new terminal.

Figure out where the Windows partitions are in the partition table. 
sudo fdisk –l

Create a new directory for the windows files
sudo mkdir /media/windows 

Mount the files
Sudo –t ntfs /dev/hda1 /media/windows

I then proceed to the file system explorer and attempt to open the file but I get a permission error.

Any help would be greatly appreciated

---

### Post by Herman on 2006-02-22
```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o umask=0222
``` :D (Herman)

---

### Post by patrick295767 on 2006-02-22
[QUOTE=Herman]```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o umask=0222
``` :D (Herman)[/QUOTE]
  
Hi Herman, 

Would you know the deep deep reason of this "-o umask=0222" ?
We all know that we have to use it ... 
but exactly what does it mean ? maybe u know & can reply... (?)

Thank you, 

Patrick

---

### Post by patrick295767 on 2006-02-22
[QUOTE=ubuntuforhumans]Hi,

I have installed ubuntu Live CD (Version 5.04) in order to retrieve files from my crashed windows 2000 machine. However when I try to open my newly created folder it is telling me I do not have permissions to view. Here are the steps I have followed;

Boot machine from Live CD and install.

Open a new terminal.

Figure out where the Windows partitions are in the partition table. 
sudo fdisk &#8211;l

Create a new directory for the windows files
sudo mkdir /media/windows 

Mount the files
Sudo &#8211;t ntfs /dev/hda1 /media/windows

I then proceed to the file system explorer and attempt to open the file but I get a permission error.

Any help would be greatly appreciated[/QUOTE]
  
In windows, plz check the two tabs in order to do ur sharing :
the first one : SHARING
the second one: SECURITY 
Put EVERYONE and ALL Things (read / write ... )

That's I am rather sure the reason

I usually do so ... and working .. !

Greetings 

Patrick

---

### Post by LordBug on 2006-02-22
[QUOTE=patrick295767]In windows, plz check the two tabs in order to do ur sharing :
the first one : SHARING
the second one: SECURITY 
Put EVERYONE and ALL Things (read / write ... )

That's I am rather sure the reason

I usually do so ... and working .. !

Greetings 

Patrick[/QUOTE]
That only works for network sharing (via CIFS or SMB), and not direct mapping like we have going on here.


I would suggest changing the mount line to:

sudo mount /dev/hda1 /media/windows/ -t ntfs -o ro,umask=0222

This will leave it locked in Read Only mode, and still grant everyone rights to it (for reading).  This way, there's no chance of accidently writing to the NTFS drive (a bad idea in Linux).

Umask is used to set permissions for the NTFS mount. 0222 is not the only value you can use, it's just one everyone knows.

---

