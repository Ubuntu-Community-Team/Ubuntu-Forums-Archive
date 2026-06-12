---
title: "Restrict User Rights"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by felin on 2007-06-13
I have two accounts on my system. Can I prevent the administrator account from being able to read files on the other. Logged in with administrator rights When i go to Home I can see the files of both users?

---

### Post by Cypher on 2007-06-13
Root can do everything on the system, Administration account is equal to root.

---

### Post by whizbaby on 2007-06-13
> **Cypher said:**
> Root can do everything on the system
Not really, what will root do when the sensible files are encrypted (or in an encrypted tar archive instead of a directory)?

---

### Post by felin on 2007-06-13
so every administrator can read each other's files?

---

### Post by whizbaby on 2007-06-13
This is neither right nor wrong. It depends on the systems settings and what you mean by saying administrator. For example you can make someone administer the printing system and install programs without giving him/her the ability to read/write/execute every file on the system (man sudoers, look at 'runas_default' or so). An admin is not necessarily equal to root. BUT in the default ubuntu installation the use of 'sudo' defaults to root and anyone in the group 'admin' will have root privileges. If you have data to hide (007?) encrypt it. If you are the main root user you can restrict the powers of admins by editing /etc/sudoers or by creating own 'admin' groups whose members will be able to do exactly what you want them to.

---

### Post by felin on 2007-06-13
> **whizbaby said:**
> This is neither right nor wrong. It depends on the systems settings and what you mean by saying administrator. For example you can make someone administer the printing system and install programs without giving him/her the ability to read/write/execute every file on the system (man sudoers, look at 'runas_default' or so). An admin is not necessarily equal to root. BUT in the default ubuntu installation the use of 'sudo' defaults to root and anyone in the group 'admin' will have root privileges. If you have data to hide (007?) encrypt it. If you are the main root user you can restrict the powers of admins by editing /etc/sudoers or by creating own 'admin' groups whose members will be able to do exactly what you want them to.
Great - explains a lot - thanks very much;)

---

