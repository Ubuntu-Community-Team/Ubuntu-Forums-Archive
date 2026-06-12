---
title: "HOW? create a user and disallow specific hdd/folder access?"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-04-01
how do i create a new user and only allow them specific access to folders/hdd's/hdd folders...
for example "john" shouldn't be able to view My Music folder? how do i let him see the rest of the hard drives contents or simply disallow him access to the entire hard drive?
is there anyway that i can do this?
i want to basically allow the user to save in their own home dir and browse the web and the apps installed but not view the hard drives/folders on the computer.or IF possible allow specific viewing of certain folders on these hard drives.

how?
cheers for any help submitted;)

---

### Post by ViRMiN on 2007-04-01
You could use the extended attributes, providing your kernel and filesystems support them?  You'll need to install the "acl" package from the Universe repository to get the setfacl and getfacl commands.  Have a read of the man pages, they should explain everything...

---

### Post by oilchangeguy on 2007-04-01
try the command, chmod 
this changes the access permissions of a file or directory. also you can right click on a file, select properties, permissions.and un-check anything for users and groups.

---

### Post by ikonia on 2007-04-01
create the correct groups for group owner ship and use chown and chmod to set the permissions up for that specific use,

---

