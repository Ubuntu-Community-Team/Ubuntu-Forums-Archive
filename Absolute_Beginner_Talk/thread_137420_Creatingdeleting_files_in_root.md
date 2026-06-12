---
title: "Creating/deleting files in /root?"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by kerunt on 2006-02-27
Hi all,
fresh Linux user here.
Just successfully installed Ubuntu after 2 days of attempts. I created a folder in /root which I wish to share with Windows computers on the network, but I cannot create any files there, and I cannot delete a folder I created through the SHARED FOLDERS tool. I get this error:
Error while deleting.
"/root/Shared" cannot be deleted because you do not have permissions to modify its  parent folder.
What does that mean? And how can I give myself the required permissions?

If it makes any difference, here is my structure:

160GB /dev/sda
- /dev/sda1 is /boot (100MB)
- /dev/sda3 is /swap (3GB)
- /dev/sda2 is / (156.9GB)


160GB /dev/sdb
- /dev/sdb1 is /home (160GB)

Any help/tips would be appreciated!
Thanks!

---

### Post by newuser111 on 2006-02-27
prefix 'sudo' to any commands requiring root access

---

### Post by kerunt on 2006-02-27
Is it possible to have root access from the File Browser?
What is the delete command for the terminal? del / delete are not regocnized...

//edit
Is there a list/site of all/standard commands supported by the terminal?

---

### Post by newuser111 on 2006-02-27
'sudo -s' will give you a root shell

press alt f2 and type 'gksudo nautilus' it will open a file browser with root access

del is a dos command, rm is the linux command rm -r will delete a directory

---

### Post by kerunt on 2006-02-27
Ah, thanks for the info :).

---

