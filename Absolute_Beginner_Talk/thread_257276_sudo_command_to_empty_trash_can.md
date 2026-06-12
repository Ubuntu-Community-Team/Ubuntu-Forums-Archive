---
title: "sudo command to empty trash can?"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-09-14
Some how I've managed to get files into my trash can that 'I don't have permission to delete'. Does anyone know of a command that empties the trash can using sudo so that files you need root permission to delete can be deleted, Or if someone knows a technique which could be used to accomplish the same goal. Thanks in advance.

---

### Post by skymt on 2006-09-14
```
sudo rm -r ~/.Trash/*
```This won't get invisible files, use ".Trash/.*" for that.

Also, be very careful. Any recursive or wildcard removal is extremely dangerous if you type it wrong. You may want to use the -i option, which makes it ask you about each item.

---

### Post by cstudent on 2006-09-14
You shouldn't have to use sudo to delete the trash in your home directory. That would be somewhat safer.

---

### Post by skymt on 2006-09-14
> **cstudent said:**
> You shouldn't have to use sudo to delete the trash in your home directory. That would be somewhat safer.

Did you even read the OP?

Just wondering.

---

### Post by cptjaben on 2006-09-14
ok, thanks for the help.

---

