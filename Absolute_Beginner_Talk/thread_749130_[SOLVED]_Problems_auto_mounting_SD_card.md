---
title: "[SOLVED] Problems auto mounting SD card"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by kahrytan on 2008-04-08
I see to be having problems mounting SD card through a USB Multi Reader.


Originally, I would plug in in reader and read/write/delete on SD card.  But now, It seems to refuse to mount it as writable drive. It keeps mounting it as read-only. 

Details: 
[LIST=1]
[*] Card is not locked, nor is the reader. Ruled it out.
[*] It is not fstab issue. Ruled it out. [I used past experience with hdd and HOWTO in forums as a guide]
[*] It is not a permissions issue. Ruled it out.[/LIST]
 Please refrain from suggesting any fstab usage since that is the underlying problem and that it has been clearly established that it is not. I want Ubuntu to stop mounting the card as READ ONLY. I am not talking about Permissions or is it FSTAB issues.

if Ubuntu continues to mount the card as read only, I will be forced to continue using Windows to write/delete files from it.


EDIT: The problem is solved. Simple Format of the SD card fixed it. Ubuntu doesn't treat the card as read only. Further proof that it was not a fstab issue.

---

