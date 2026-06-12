---
title: "normal user to superuser"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by masumcis on 2006-08-11
how can i change a normal user to a root user. what is the command. plz i can't go for root mode. windomode can not give me access to the pc.](*,)

---

### Post by Cone on 2006-08-16
I'm not quite sure about how to do this, but I'm sure any one experienced with Linux will tell you this is a no-no.

If you want to run the file explorer (nautilus) in super user mode, type "gksudo nautilus" in the terminal and you can do that.

The preferred method, though, is to learn the way around the terminal at least a little bit, and "sudo *command*" whenever there's a command that you need done on a restricted access directory/file/device.

Some basic commands if:
cp <file1> <file2> - copies <file1> and renames the copy as <file2>
rm <file> - deletes <file>
cd <path> - navigates to a path
ls - lists the files and directories in the current path

Add sudo in front of any of those if you need to mess with restricted files.

Hope this helps at least a little bit, and good luck.
~Cone

---

