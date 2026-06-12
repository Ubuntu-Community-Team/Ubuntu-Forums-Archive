---
title: "How to change read/write permisson ??"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by GoranI on 2007-06-25
I installed Ubuntu 7.04 with wubi installer. It is installed on second partition of my hd - it is vfat. How to change permision to write on this disk (it is mounted).When I open some text file, I make some change, and when I try to save it on this disk it says that i don`t have permission. I checked and "root" is owner of this disk. I logged as root but I don`t know how to change ownership for other account for example for user account.

Thanx for helping !! :)

---

### Post by Happy_Man on 2007-06-25
Well, log in as yourself, and enter the command ```
gksudo nautilus
``` Navigate over to the folder where your drive is located, right-click, and choose properties. Go to the permissions tab, change the owner and group to yourself, allow read/write access, and close. That should do it!

---

### Post by GoranI on 2007-06-25
> **Happy_Man said:**
> Well, log in as yourself, and enter the command ```
gksudo nautilus
``` Navigate over to the folder where your drive is located, right-click, and choose properties. Go to the permissions tab, change the owner and group to yourself, allow read/write access, and close. That should do it!

I have nautilus installed, and I cannot change permission from there, on permission tab everything is disabled, I can`t change anything...

---

### Post by technomaniac on 2007-06-25
sudo mount -t vfat /dev/hdax /media/windowsdrive -w

where /dev/hdax---replace x with the partition number of the drive you want to mount. For SCSI and SATA it will be /dev/sdax

/media/windowsdrive--the directory where you want to mount it

---

