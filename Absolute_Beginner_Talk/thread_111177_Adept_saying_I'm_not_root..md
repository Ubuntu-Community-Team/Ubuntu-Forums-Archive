---
title: "Adept saying I'm not root."
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by equal on 2006-01-01
I'm logging into Adept, and it's saying the following message:

"The APT Databse will be opened in read-only mdoe, this means you cannot install/uninstall/upgrade anything/ You have to run this program as root to be able to do that."

This was never an issue in gnome. What's going on?

---

### Post by scaine on 2006-01-01
I've never come across Adept before, but from the message it's giving you, it sound like a front end for apt-get.

You'll need to run this as root.  In Ubuntu, you'll need to use the command "sudo", since Ubuntu doesn't use the root user.  Sudo is just short for "Supervisor Do" and it acts out the command with root privileges.

Open a terminal and type "sudo adept" (assuming Adept is started by "adept").
When you're prompted for a password, enter your own password.  As long as you are defined as a Sudo'er, the command will work (if you installed Ubuntu normally, you will be a sudo'er by default).

---

