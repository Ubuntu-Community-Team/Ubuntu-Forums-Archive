---
title: "define user as root?"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by anubis2814 on 2006-07-21
how do I define the user as root for installation purposes?  I'm sure its simple.

---

### Post by Kilz on 2006-07-21
> **anubis2814 said:**
> how do I define the user as root for installation purposes?  I'm sure its simple.

sudo command

---

### Post by anubis2814 on 2006-07-21
can you be more specific please? I'm very new

---

### Post by Fac51 on 2006-07-21
open a terminal window
type in:

sudo -i

press enter

it will want you to enter your regular user password and then you will be switched to root

---

### Post by suhaswadkar on 2006-07-21
for security reasons, root account is disabled in ubuntu. whenever u need to do something with root previlages, use sudo command. eg, if u need root powers to create a directory (mkdir), use- $sudo mkdir /dir_name/
    if u don't want to type sudo every time, just type $su -   at terminal, provide your password & u'll be logged on as root. do the stuff & logout.
    WARNING- root is very powerfull & may damage ur system if u r not carefull. that's why it's disabled in the first place.

---

### Post by Fac51 on 2006-07-22
> **suhaswadkar said:**
> for security reasons, root account is disabled in ubuntu. whenever u need to do something with root previlages, use sudo command. eg, if u need root powers to create a directory (mkdir), use- $sudo mkdir /dir_name/
    if u don't want to type sudo every time, just type $su -   at terminal, provide your password & u'll be logged on as root. do the stuff & logout.
    WARNING- root is very powerfull & may damage ur system if u r not carefull. that's why it's disabled in the first place.

'su -'   <--- does not work unless you first do 'sudo passwd root' which would defeat the purpose of have no root user.... hence i previously suggested 'sudo -i' followed with no command

Example:
```
user@localhost:~$ sudo -i
Password:
root@localhost:~#
```

---

### Post by 3rdalbum on 2006-07-22
"sudo su" and "sudo bash" also work in the same way.

If you want to get back to your normal user terminal, type "exit".

---

