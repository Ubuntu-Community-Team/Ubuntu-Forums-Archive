---
title: "User with Sudo previlges"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by praveenpg on 2006-08-08
Hi,

I am new to Linux and wanted a help. I deleted the user id created during the install (sudo user) by mistake and unable to perform any adminstrative tasks. Is there anyway I can create a new sudo user or get access to su password.

Praveen

---

### Post by hopstah on 2006-08-08
under System > Administration > Users and Groups, modify the properties of any user, and click on the furthest right tab called 'User Privileges'.  Check the box titled 'Executing System Administration Tasks' and you should be all set.

---

### Post by hw-tph on 2006-08-08
You probably cannot do what hopstah suggested if you don't have sudo access. Boot into recovery mode (usually referred to as "Linux single user mode" but the name is dumbed down in Ubuntu). You will find yourself at the shell prompt as root. First make a backup of /etc/group, then either run **adduser username admin** (replace "username" with your actual username) or edit /etc/group and add your username to the admin line, like this:```
admin:x:112:username
```
This line contains a comma-separated list of usernames so you can add multiple users to the admin group like this: ```
admin:x:112:bob,john,steve
```

Reboot and you're set.

Håkan

---

### Post by praveenpg on 2006-08-08
Hope I am not asking something stupid. How can we boot into Linux single user mode? Please bear with me as I am new to Linux.

Praveen

---

### Post by praveenpg on 2006-08-08
> **hw-tph said:**
> You probably cannot do what hopstah suggested if you don't have sudo access. Boot into recovery mode (usually referred to as "Linux single user mode" but the name is dumbed down in Ubuntu). You will find yourself at the shell prompt as root. First make a backup of /etc/group, then either run **adduser username admin** (replace "username" with your actual username) or edit /etc/group and add your username to the admin line, like this:```
admin:x:112:username
```
This line contains a comma-separated list of usernames so you can add multiple users to the admin group like this: ```
admin:x:112:bob,john,steve
```

Reboot and you're set.

Håkan
Hope I am not asking something stupid. How can we boot into Linux single user mode? Please bear with me as I am new to Linux.
 
 Praveen

---

### Post by Malac on 2006-08-08
It should be on your boot menu at the beginning.
It should say "(Recovery Mode)" at the end of a line the same as your normal boot kernel.

---

### Post by aysiu on 2006-08-08
This gives full instructions:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by praveenpg on 2006-08-08
Thanks everyone. I finally managed creating a sudo user.

Regards,
Praveen

---

