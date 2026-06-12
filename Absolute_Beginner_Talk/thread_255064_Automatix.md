---
title: "Automatix"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by snagger on 2006-09-10
Hi need help, finaly installed ubuntu and its looking good.

But trying to install automatix ([www.getautomatix.com](www.getautomatix.com)) 

Ive got to a point where i have to type my password but it wont allow me to type or paste any ideas?

---

### Post by blackened on 2006-09-10
At the password prompt the terminal is still getting the characters, it's just not echoing them back to be read by all. This is for security in case anyone is looking over your shoulder at the screen.

Just enter your password as normal (watch those typos), and press enter. Should get you going normally.

---

### Post by snagger on 2006-09-11
Right, what password am i supposed to be typing in in the space? Is it my log on password? or is it one i need to get from automatix?
This is the password screen that i see:

---

### Post by snagger on 2006-09-11
Sorry forgot to attach

---

### Post by xyz on 2006-09-11
I type my log-on password. I've got only 1 user, 1 password.
Should work for you.

---

### Post by Metacarpal on 2006-09-11
You'll need to type your login password.

Here's why it's asking for your password:
There are two basic types of changes you can make to your system: Personal, which only affect your login and are mostly look-and-feel types of changes, and Administrative, which covers everything from setting up networking to installing software.

In other Linux distros, you have to log in under a special "root" user account to make major system changes, or give your login "superuser" privileges.  That can be dangerous, because when acting as root it's all too easy to make a mistake that can mess up the operating system.

To prevent that, Ubuntu uses a command called sudo.  This allows you to execute one task with administrator privileges, which seriously reduces the likelihood that you'll break your installation.

For more info, [read this]("https://help.ubuntu.com/community/RootSudo")

---

