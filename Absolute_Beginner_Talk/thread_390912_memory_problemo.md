---
title: "memory problemo"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Cardmaster91 on 2007-03-22
hi, one day my ubuntu is working fine. the next, no. It says that there isn't enough space to login or sumtin. I realized then that when i had restarted the computer, i had just finsihd riping a few dvds. So, how do i clear up some of this space?

---

### Post by Zuuswa on 2007-03-22
Well, if indeed you are out of hard drive space, simply delete some files you dont need anymore.  Login using a failsafe terminal, and delete some files.

---

### Post by Cardmaster91 on 2007-03-22
i know i must delete files, but how do i get onto the computer to delete the files? whats a failsafe terminal?

---

### Post by Zuuswa on 2007-03-22
Before you log in, there should be a button that says options or sessions, either way select the failsafe session and login.  Or you can reboot the machine and choose the recovery mode kernel in grub.  Then use the command 'cd' to **c**hange **d**irecectory, the command 'ls' to list the files in the current directory, and 'rm' to delete a file.

```
cd new/directory/
rm directory/unwantedfile
```

but be careful, because if you are running as root, rm can be a dangerous tool.  Dont delete important system files as this will bork your installation and you will have to re-install!

---

