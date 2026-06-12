---
title: "rdesktop"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2007-08-17
easy question but for some reason i can't figure it out.  I'm using rdesktop to log onto my windoz computer.  everytime i log on i have to enter my user name and password, I prefer not to have to do this everytime.  So my question is how to you make it so you don't have to type everytime

---

### Post by nexu56 on 2007-08-17
rdesktop -u <username> -p <password> <ipaddress>

Incidentally you can get the options for almost any command by adding --help to the command. e.g. rdesktop --help

---

