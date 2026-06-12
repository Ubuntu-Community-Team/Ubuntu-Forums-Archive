---
title: "Just a quick question"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Skittle on 2007-11-13
I've been reading a lot of manuals and help sites, being completely new to Linux, and this came up in my mind.

1. What is the difference between Su and Sudo?

2. Is there a difference between rm -rf and rmdir?

---

### Post by mkoehler on 2007-11-13
Skittle,

-"su" means switch user.  This is useful if you want to switch to the root user instead of always having to type "sudo" (or you can switch to any other user).

-"sudo" means that you're running a command with root permissions (as the currently logged on user).  If you want to run a command with root permissions as the root user, use "gksudo".

----------------------------------------------------------------------------------------------------------------------------

-"rm -rf" means remove a file/folder recursively/forcefully.  This is useful if you want to remove a directory with files inside of it, i.e. you could use rm -r <directory_name>.

-"rmdir" means remove a directory.  Unfortunately, if you have files inside of the directory, running the "rmdir" command will result in errors.  Therefore, I recommend that you stick to the "rm" command.

Cheers!

---

### Post by Skittle on 2007-11-13
> **mkoehler said:**
> Skittle,

-"su" means switch user.  This is useful if you want to switch to the root user instead of always having to type "sudo" (or you can switch to any other user).

-"sudo" means that you're running a command with root permissions (as the currently logged on user).  If you want to run a command with root permissions as the root user, use "gksudo".

----------------------------------------------------------------------------------------------------------------------------

-"rm -rf" means remove a file/folder recursively/forcefully.  This is useful if you want to remove a directory with files inside of it, i.e. you could use rm -r <directory_name>.

-"rmdir" means remove a directory.  Unfortunately, if you have files inside of the directory, running the "rmdir" command will result in errors.  Therefore, I recommend that you stick to the "rm" command.

Cheers!

Thank you So much :)
I've been a member of this community for only 4 or 5 days and I already love it to death!

---

