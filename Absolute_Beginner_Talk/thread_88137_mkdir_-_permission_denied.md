---
title: "mkdir - permission denied"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by cbeshears on 2005-11-09
I am very new to Ubuntu and I am trying to learn how to make a new directory using the command line interface.  I am typing: "mkdir /projects" while I'm in the root directory.  It then tells me, "cannot create directory '/projects': Permission denied"
Can anybody tell me what I'm doing wrong?  Any help is greatly appreciated.  Thanks.

---

### Post by 23meg on 2005-11-09
Add "sudo" as a prefix to the command and you'll be set. When you add sudo, you become root (superuser) during the execution of the command so you have privileges to modify files you can't normally access as a normal user. The Ubuntu default is that users can only modify their own home directories.

---

### Post by cbeshears on 2005-11-09
Okay.  It "appeared" to have worked since it didn't give me any error messages, but when I list the contents of the directory (ls) it doesn't show up.  I'm so confused... :confused:

---

### Post by Kvark on 2005-11-09
While you are in the directory you want to place the projects directory in, type "mkdir projects". Note that there should be no "/" in front of the name. "/projects" is an absolute path because it starts with "/" and will always mean exactly "/projects" instead of "/your/current/location/projects"

BTW. You really should put your projects directory together with your other files in your home directory.

---

### Post by aysiu on 2005-11-09
[QUOTE=cbeshears]Okay.  It "appeared" to have worked since it didn't give me any error messages, but when I list the contents of the directory (ls) it doesn't show up.  I'm so confused... :confused:[/QUOTE] Should there be any contents in a directory you just created? I'm confused now.

---

### Post by cbeshears on 2005-11-09
Got it!  I was putting the "/" in front of the directory name.  I understand now.  Thanks for helping me clear it up.

---

