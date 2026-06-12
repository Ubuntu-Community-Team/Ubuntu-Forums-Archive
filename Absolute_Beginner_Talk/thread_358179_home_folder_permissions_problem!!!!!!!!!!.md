---
title: "home folder permissions problem!!!!!!!!!!"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by The55Gon on 2007-02-10
okay so the other day i formatted one of my partitions as ext3 to use as the linux /home partiton. i put all the files i wanted to save on it. Then i installed ubuntu. i set that partition as the home folder. When i boot up linux, i navigate to the home folder and see all my files there, plus a "The55Gon" folder. The problem is, i can't move all my files from home to home/The55Gon. The error message reads "Error while moving. '/home/Documents' cannot be moved because you do not have permissions to change it or its parent folder."

i just started ubuntu, so i really suck at this. is there a way i can get the permission to do this?

thanks

---

### Post by spin2cool on 2007-02-10
you need to become familiar with two commands:

sudo, which allows you to do things as a superuser, which gives you permission to do anything.

chmod, which allows you to change the permissions of a file.
The arguments to chmod are who you want to have permission:
 u = user, g = group, o = others

then a + or - sign, depending on whether you want to add or remove permissions

Lastly, the permissions you want to allow
r = read
w = write
x = executable

So, if I wanted to allow myself to read and write to a file, I'd type:
```
sudo chmod u+rw <filename>
```

to allow yourself access to everythign in your home directory, you want to do something like:
```
sudo chmod u+rw *
```

---

