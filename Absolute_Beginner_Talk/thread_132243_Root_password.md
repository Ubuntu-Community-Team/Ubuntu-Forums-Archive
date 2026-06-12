---
title: "Root password"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by epolson on 2006-02-17
While installing ubuntu, I was not (or at least don't remember being) prompted for a root password.  What is the default password for the root user?

---

### Post by aggiechemist on 2006-02-17
Ubuntu tries hard to avoid ever using the root user. Instead, the first user you signed up should have the power to be super user with the sudo command. Say you want to run, just as an example, apt-get. Then to do the as super user the command is just

sudo apt-get upgrade

and then type the password for the user you are logged in as. If you really want into root, then go check the login settings and there should be one to allow root login(System, Administration, Login Setting, Security tab), and I think it will have that first users password as well. But generally it is not neccesary.

---

### Post by Jucato on 2006-02-17
The ever useful link:

[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

