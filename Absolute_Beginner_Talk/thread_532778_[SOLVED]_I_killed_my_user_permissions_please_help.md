---
title: "[SOLVED] I killed my user permissions please help ??"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Ray190e on 2007-08-23
I was very smart and changed my user permissions ,this I now realized was a very dumb idea as now I cant change it back .How can I fix this brilliant idea ?The system/administration drop down menu does not have the user group menu in it any more .PLEASE HELP ME ?

---

### Post by ddrichardson on 2007-08-24
Do you still have sudo rights - open a terminal and type sudo to find out.

---

### Post by WebSiteGuru on 2007-08-24
ddrichardson  probably not going to have that right, if the system was log off or rebooted.

Reboot and try going to recovery mode (it will give you root access) and try to get you access back from there by using sudo command. I dont know exactly how to use the command so you might have to search for it. Or someone may be able to tell you the sudo command.

---

### Post by aysiu on 2007-08-24
This may help you recover *sudo* if you lost it:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

However, you should explain exactly how you changed the permissions; otherwise, we won't know how to tell you to change it back.

---

### Post by Ray190e on 2007-08-25
I fixed it :) here is how i did it 
1. open terminal and typed "su"
this asked me for a password , I entered my root password
2. then typed "gksudo user-admin" ,this gave me the the users and groups menu to fix me mess.

Thanks for the Help]

---

### Post by aysiu on 2007-08-25
If you're root, you don't need *gksudo*. You could have done: ```
su
users-admin
``` If you're using *sudo* properly, you do ```
gksudo users-admin
``` without the *su*.

---

### Post by ddrichardson on 2007-08-25
Glad its all working. Marking the thread as solved will help other users with the same problem.

UAResolved

---

### Post by Ray190e on 2007-08-25
Thanks again for the help:guitar:

---

