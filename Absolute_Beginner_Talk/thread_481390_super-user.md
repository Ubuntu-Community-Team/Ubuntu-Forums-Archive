---
title: "super-user?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by noobbutnotboob on 2007-06-22
hilariously basic question but I just ran the 'lshw' command and got the message "warning: you should run this program as a super-user". What does that mean? :redface:

---

### Post by Jimmyfj on 2007-06-22
It means that you need to run the command as root:

su
password:

---

### Post by LaRoza on 2007-06-22
Type sudo before the command.

---

### Post by noobbutnotboob on 2007-06-22
oh that's embarassing! thanks LaRoza and Jimmy!

---

### Post by LaRoza on 2007-06-22
Running as root is not recommended unless you have to, like when install or preforming administrative functions.

"sudo" runs the command as root, su will make every command you run in that terminal run as root, not usually recommended. 

"gksudo" should be used for graphical apps, like if you wanted to run nautilus as root.

When you type your password, you will not see anything like *, so don't worry.

---

### Post by LaRoza on 2007-06-22
> **noobbutnotboob said:**
> oh that's embarassing! thanks LaRoza and Jimmy!

Don't be embarrassed. No one is born with that knowledge and the concept is foreign to Windows users, where every command is run as root (in an administrative account). This way, you cannot accidentally run something as a super user (root, admin, administrator).

---

