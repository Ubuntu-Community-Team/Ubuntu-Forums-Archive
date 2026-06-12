---
title: "superuser"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by inspiron on 2007-02-01
I try to install a program and therefore I need to be logged in as su. What is the default password for su. I have recently installed ubuntu and I never got to type a password for su. Only for the user Im using now. I have tried the same password I decided during the installation for the user Im using now and I have tried to let password be empty but it wont work.
What is the password?
Thanks in advance.

edit: I got to a solution on my own, by typing "sudo command" and then password.

---

### Post by Paerez on 2007-02-01
Yep. Su = the command to turn into the user called Root (which means Admin in linux). Root's password is scrambled by default for security. Whenever you need to do something as admin, you sudo it (get it? do as su). That *temporarily* makes you root, which is safer.

---

### Post by Brunellus on 2007-02-01
for help with this, read this page:

[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

