---
title: "Can't see Hard Drives"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by LeeDJC on 2006-03-31
I've just installed Kubuntu, but I can't see my other two hard drives? One is a  IDE FAT32 40gig and the other is a SATA NTFS 250gig. I want to be able to convert these to proper linux as well at some point. Do I need to mount these manually?

Cheers

---

### Post by pbaehr on 2006-03-31
This guide should help you:
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

It walks you through mounting ntfs and fat32 drives.

---

### Post by Princey on 2006-03-31
[QUOTE=LeeDJC]I've just installed Kubuntu, but I can't see my other two hard drives? One is a  IDE FAT32 40gig and the other is a SATA NTFS 250gig. I want to be able to convert these to proper linux as well at some point. Do I need to mount these manually?

Cheers[/QUOTE]

Yes you do. Here's a post that can give you a guide [http://www.ubuntuforums.org/showpost.php?p=846579&postcount=8]("http://www.ubuntuforums.org/showpost.php?p=846579&postcount=8"). It's written for FAT32 but for the NTFS one, just replace with this code> /dev/hda6       /location/folder  ntfs    nls=utf8,umask=0222 0       0 where you substitute location/folder for where you want to mount the files eg. /media/myntfsdrive. Be sure to make the directory first. Don't mount both into the same directory. Of course, replace hda6 with whatever is the device name. 

For the link above, you don't have to go with osshare. I prefer use native names like winntfs or winfat. It's all left up to you.

---

### Post by LeeDJC on 2006-03-31
OK, I got as far as the ```
sudo gedit /etc/fstab
``` line, but get the error ```
sudo: gedit: command not found
``` :(

---

### Post by Princey on 2006-04-22
[QUOTE=LeeDJC]OK, I got as far as the ```
sudo gedit /etc/fstab
``` line, but get the error ```
sudo: gedit: command not found
``` :([/QUOTE]

Just restumbled across your thread again. Sorry for the long delay. Just wanting to know did you get the problem solved?

---

### Post by aysiu on 2006-04-22
Kubuntu uses *kwrite*, not *gedit*.

---

### Post by Princey on 2006-04-22
[QUOTE=aysiu]Kubuntu uses *kwrite*, not *gedit*.[/QUOTE]

kate would even be an easier choice to use instead of kwrite or kedit. I think with Kubuntu, kate is the default text editor.

---

