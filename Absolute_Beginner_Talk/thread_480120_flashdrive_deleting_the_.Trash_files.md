---
title: "flashdrive deleting the .Trash files?/"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by johntkucz on 2007-06-21
Hello, I am trying to delete the (hidden) .Trash files on a flash drive get the error that it's a read-only file system

ubuntu@ubuntu:/media/TRAVEL2GB$ sudo rm .Trash-ubuntu
rm: cannot remove `.Trash-ubuntu': Read-only file system
ubuntu@ubuntu:/media/TRAVEL2GB$ rmdir .Trash-ubuntu
rmdir: .Trash-ubuntu: Read-only file system
ubuntu@ubuntu:/media/TRAVEL2GB$ 

Help!!

---

### Post by deadgobby on 2007-06-21
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_files.2Ffolders_permissions](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_files.2Ffolders_permissions)

---

### Post by johntkucz on 2007-06-21
um, thanks gobby, appreciate the response, but Im a bit too much of  noob for such a concise reference.

I tried to change permissions and folder access is "create delete", file access is "--".  When I change the file access, it doesn't "stick"; it just reverts back to"--". when I reopen the permissions window.

bTw, [www.microsuck.com](www.microsuck.com) looks like a cool site.

---

### Post by johntkucz on 2007-06-21
Will i have to reformat the flashdrive?  Want to avoid that and just find a way to empty the trash!

---

### Post by johntkucz on 2007-06-21
It still says Read-only file system error even with sudo chown


ubuntu@ubuntu:/media$ sudo chown root TRAVEL2GB
chown: changing ownership of `TRAVEL2GB': Read-only file system

---

### Post by abrar-ahmed on 2007-06-21
make sure the drive is mounted read write (rw)

---

### Post by Freelance Physicist on 2007-06-23
Is the flash drive formatted as NTFS?  If so,

```
$ sudo apt-get install ntfs-config
```

Then, go to the applications menu and select System Tools -> NTFS Configuration Tool

Select both "Enable write support for internal device" and "Enable support for external device"

After this you should be able to delete files off the drive (as well as create and edit them, too)

---

