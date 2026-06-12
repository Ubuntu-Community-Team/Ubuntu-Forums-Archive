---
title: "Why cant i switch user to root????"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by sketchone on 2007-01-22
been trying for ages, everytime i try with the correct password from my user acount and it just says authentification failed!??

i cant open samba with out it

any ideas

thanks

---

### Post by meng on 2007-01-22
Root user is not enabled by default.
We use 'sudo' instead.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tonyr1988 on 2007-01-22
Is there a specific task you can't use sudo for?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In Ubuntu, you don't use root, you use sudo for specific commands.

Or, use

> sudo -i

to open a terminal to do root things in.

---

### Post by ComplexNumber on 2007-01-22
how exactly are you going about it?

---

### Post by tomBorgia on 2007-01-22
Hiya, you'll need to open a terminal and type:

sudo passwd root

(this will then ask you for your password, then a new password for root)

The root password is not set (the account is locked out) for security reasons... after setting the password (the passwd command) you can log in as root.

Tom.

---

### Post by sketchone on 2007-01-22
thanks very much that was very helpfull

---

