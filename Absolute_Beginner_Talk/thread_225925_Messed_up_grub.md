---
title: "Messed up grub"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by bamend on 2006-07-30
I messed up my grub login when I set the default to 6.  I was trying to default to Windows which was the seventh item listed in my grub.list file.  Now when I boot up I get the grub menu and nothing else.  How can I get out of this?

---

### Post by x64Jimbo on 2006-07-30
You have to start with zero. First entry is 0, second is 1, etc.

---

### Post by bamend on 2006-07-30
How do I get there from the grub screen I get at bootup?

---

### Post by x64Jimbo on 2006-07-30
Boot your install disc and edit it from there.
it'll be in your primary hard disk under boot/grub/menu.lst

---

### Post by bamend on 2006-07-30
How do you get to the hard disk? my hdb1?

---

### Post by x64Jimbo on 2006-07-30
Depends on where you installed Ubuntu. Most of the time, if ubuntu is your only OS, it'll be on hda1. If you have Windows installed first and then installed ubuntu next to it, it's probably hda2. If you have a SATA HDD, replace "hd" in "hda1" with "sd"

---

### Post by Herman on 2006-07-30
> I messed up my grub login when I set the default to 6. I was trying to default to Windows which was the seventh item listed in my grub.list file. Now when I boot up I get the grub menu and nothing else. How can I get out of this?
bamend  , You should be able to run your Dapper 'Desktop' Live/Install CD or some other Live CD and mount your installed Dapper filesystem and access your /boot/grub/menu.lst and fix the problem.

Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD...........GO

Just click on 'GO' above. It even has how to open menu.lst included.

By the way, we can type 'saved' (without the inverted commas) instead of a number to replace the '0'. Then Grub will boot the last-booted operating system it remembers by the 'savedefault' command in each operating system entry.
```
default     saved
```
If you 'comment out' all the other entries 'savedefault' commands by placing a # (hash mark) in front of 'savedefault',(to make it *not* save the ones you *do not* want booted by default).
```
# savedefault
```
 it will only remember the one without the #. That seems to me like a better way to set the default operating system. It's not the conventional way but it might be better since when you get an update with a new kernel and the number of entries in your list changes you won't need to re-edit.
Regards, Herman :D

---

### Post by x64Jimbo on 2006-07-30
You may also want to keep a backup of your menu.lst since it gets overwritten with each new kernel update and it makes booting any other OS difficult until you can re-write the boot options for them.
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

---

