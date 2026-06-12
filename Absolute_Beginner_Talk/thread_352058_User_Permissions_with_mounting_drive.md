---
title: "User Permissions with mounting drive"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by CryptiniteDemon on 2007-02-02
Okay I finally got this hard drive mounted, but I cannot access it for the life of me.  It just keeps telling me I don't have the permissions necessary to view its contents.

Here's the line I have in my fstab file

/dev/sda5  /media/StorageDrive  ntfs   ro,user,auto     0           0


It shows the correct size for the drive and the space I've used on it, but I just can't get into the thing.

---

### Post by logos34 on 2007-02-02
try 
> /dev/sda5 /media/StorageDrive ntfs ro,auto,user,fmask=0111,dmask=0000 0 0

or 
> /dev/sda5 /media/StorageDrive ntfs defaults,nls=utf8,umask=007,gid=46 0 0

---

### Post by logos34 on 2007-02-02
> It shows the correct size for the drive and the space I've used on it,

what shows it?

---

### Post by Gerard Barberi on 2007-02-02
If you have Samba installed (if not, sudo apt-get install samba smbfs)...

gksudo gedit /root/.smbcredentials

put into the file

username=your username 
password=your password

save it, then...

sudo chmod 700 /root/.smbcredentials
gksudo gedit /etc/fstab

add to it

/dev/sda5 /media/StorageDrive smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0

remount fstab

sudo mount -a

this will allow you to read/write to the drive and mount it on boot

if you just want read access, then do not include "dmask=777,fmask=777" in fstab

---

### Post by jkeyes0 on 2007-02-06
> **Gerard Barberi said:**
> If you have Samba installed (if not, sudo apt-get install samba smbfs)...

gksudo gedit /root/.smbcredentials

put into the file

username=your username 
password=your password

save it, then...

sudo chmod 700 /root/.smbcredentials
gksudo gedit /etc/fstab

add to it

/dev/sda5 /media/StorageDrive smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0

remount fstab

sudo mount -a

this will allow you to read/write to the drive and mount it on boot

if you just want read access, then do not include "dmask=777,fmask=777" in fstab

<3 you.... <3 you so much. :) :) :)

---

### Post by OisinT on 2007-09-12
> **Gerard Barberi said:**
> If you have Samba installed (if not, sudo apt-get install samba smbfs)...

gksudo gedit /root/.smbcredentials

put into the file

username=your username 
password=your password

save it, then...

sudo chmod 700 /root/.smbcredentials
gksudo gedit /etc/fstab

add to it

/dev/sda5 /media/StorageDrive smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0

remount fstab

sudo mount -a

this will allow you to read/write to the drive and mount it on boot

if you just want read access, then do not include "dmask=777,fmask=777" in fstab

For some reason this didn't work for me.  Any and all help is appreciated.  I think both of my hard drives are screwed up... I dont even know where to start.

---

### Post by Gerard Barberi on 2007-09-12
> **OisinT said:**
> For some reason this didn't work for me. Any and all help is appreciated. I think both of my hard drives are screwed up... I dont even know where to start.
Sorry, Looking at my previous post, I realized that was for network drives. Try this and see if it works
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

