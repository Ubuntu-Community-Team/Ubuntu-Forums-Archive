---
title: "mp3 player"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by joot211 on 2007-09-18
I have a graig usb mp3 player. All has worked fine, but since I put kde and enlightenment on, I can´t write, erase, or do much of anything besides play the music. Every time I try to change the permissions for /media/disk, or any file on the mp3 player I get the message read only. When I try todo this as root I get the message, ¨Could not change permissions for /media/disk/02 - Forsaken.mp3¨ Can anyone help?

---

### Post by gautada on 2007-09-18
> **joot211 said:**
> I have a graig usb mp3 player. All has worked fine, but since I put kde and enlightenment on, I can´t write, erase, or do much of anything besides play the music. Every time I try to change the permissions for /media/disk, or any file on the mp3 player I get the message read only. When I try todo this as root I get the message, ¨Could not change permissions for /media/disk/02 - Forsaken.mp3¨ Can anyone help?

What is the user:group for the device?  Are you using the proper User Privileges in System->Administration->Users and Group?

---

### Post by joot211 on 2007-09-18
permissions all look good. owner can read and write annd the account I´m on is the owner.
on the other hand I can´t do anything but read

---

### Post by joot211 on 2007-09-18
[attach]43763[/attach]

---

### Post by gautada on 2007-09-19
Is the mount done as read-only in fstab.

---

