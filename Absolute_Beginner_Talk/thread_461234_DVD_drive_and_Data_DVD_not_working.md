---
title: "DVD drive and Data DVD not working"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by leo7068 on 2007-06-01
I wanted to install World Of Warcraft quickly without waiting for updates and installs. I copied the full directory from WinXP Program Files/WoW onto a DVD, to later copy back to Ubuntu, after reformatting and installing Ubuntu. 

When I place the data DVD in the drive it told me Unable to mount, so I installed 2 things from Synaptic that looked like NTFS read/write addons. These didn't work. I could see the drive, but errors when opeing it.

I followed the steps on this website: [http://doc.gwos.org/index.php/Mount_...e_Dependencies](http://doc.gwos.org/index.php/Mount_...e_Dependencies)

However, at the last commands I used some "common sense" coding for my dvd drive. Below is what I did.

gksudo gedit /etc/fstab :

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=6f55f8df-69c6-499a-8227-89f447d19769 / ext2 defaults,errors=remount-ro 0 1
# /dev/hda5
UUID=0135fc18-d7ed-4055-9649-9f9a6e19cf9c none swap sw 0 0
/dev/hdc /media/hdc ntfs-fuse auto,gid=1001,umask=0002 0 0

I verified that I was in the NTFS group, but now I don't even see my DVD drive! Please help. I thought Ubuntu would be able to use Data DVDs made in Windows XP?

---

### Post by Damanther on 2007-06-17
It would probably be better if you installed WINE, and then ran the WoW install from wine.

Yes, it will have to redownload updates, but you'll have much better luck in the end I believe.

Mike

---

