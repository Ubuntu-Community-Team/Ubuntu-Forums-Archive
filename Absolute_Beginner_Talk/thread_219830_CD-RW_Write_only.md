---
title: "CD-RW Write only?"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-07-20
When I try to blank a CD-RW gnomebaker just freezes and K3B tells takes a couple minutes and then tells me it is write only.  The strange this is that I can burn .iso files to CD-Rs fine, why are CD-RWs not working?

---

### Post by avtolle on 2006-07-20
This seems to be related to permissions. You are trying to blank CD-RWs, as I understand it. So, I would suggest that you check the permissions for the files on the disk to be blanked, and change them as necessary, so that you have write permission for each file extant thereon. Right click the file, click on properties, and proceed therefrom. If the CD-RWs are "blank" to begin with, this could be related to how the drive is mounted. For some reason, cannot think of the terminal command to check this. HTH.

---

### Post by OU812 on 2006-07-20
I wonder if you need a package for blanking cdrws? I found a package in the repo: "udftools." Here's the homepage link:

[http://sourceforge.net/projects/linux-udf/](http://sourceforge.net/projects/linux-udf/)

john

---

### Post by fatsheep on 2006-07-20
> **avtolle said:**
> This seems to be related to permissions. You are trying to blank CD-RWs, as I understand it. So, I would suggest that you check the permissions for the files on the disk to be blanked, and change them as necessary, so that you have write permission for each file extant thereon. Right click the file, click on properties, and proceed therefrom. If the CD-RWs are "blank" to begin with, this could be related to how the drive is mounted. For some reason, cannot think of the terminal command to check this. HTH.

Yes that is correct, I am trying to blank a CD-RW that has data on it (a burned .iso image).  I have tried changing the permissions on the CD-RW itself and on the files inside it using the > sudo nautilus and > gksudo nautilus commands in the terminal.  However I continue to get messages like this when I attempt this:

> Couldn't change the permissions of "isolinux" because it is on a read-only disk

and this:

> Couldn't change the permissions of "cdrom0" because it is on a read-only disk

---

