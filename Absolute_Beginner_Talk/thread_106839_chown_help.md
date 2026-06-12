---
title: "chown help"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by c2483 on 2005-12-21
this is driving me crazy

i generated files to burn to dvd
the files had my username as owner
i could burn them from the terminal with a command

i moved the generated files to a different hard disk
now they have root as owner
i can't burn them even with sudo

i tried o change the owner back to me
sudo chown -R charles.charles /media/sda1/dvd/

it doesn't work
it goes through all the files and says operation not permitted
so how do i do it

---

### Post by cwaldbieser on 2005-12-21
[QUOTE=c2483]this is driving me crazy

i generated files to burn to dvd
the files had my username as owner
i could burn them from the terminal with a command

i moved the generated files to a different hard disk
now they have root as owner
i can't burn them even with sudo

i tried o change the owner back to me
sudo chown -R charles.charles /media/sda1/dvd/

it doesn't work
it goes through all the files and says operation not permitted
so how do i do it[/QUOTE]

Well, you can't change the permissions/owners on the DVD because it is probably read only.

If you open up a root shell or a root nautilus browser, you could probably copy them and change the permissions/owner of the copies, though that may be a bit heavy-handed.

I am guessing that your DVD is just mounted in a way that the permissions/ownership is set to root.  Put the DVD in your drive, open up a terminal and post back the results of this command to determine how your DVD is being mounted:
```

$ mount

```

---

### Post by c2483 on 2005-12-21
its not a dvd the directory is just named dvd

---

### Post by cwaldbieser on 2005-12-21
[QUOTE=c2483]its not a dvd the directory is just named dvd[/QUOTE]
Hmm, well, how did you copy the files from their original location to the second hard drive?  Also, what type of filesystem is the drive they were copied to?  How is it mounted?

---

### Post by c2483 on 2005-12-21
nevermind

---

