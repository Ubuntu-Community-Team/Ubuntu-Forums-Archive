---
title: "What is root?"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by misfito on 2007-01-25
Hello every1 I new at this and I want to know what root is and how to avoid making something bad to my system by installing things as root.

---

### Post by mykalreborn on 2007-01-25
root is the administrator user. it's not a program you can install. think of it as the user who can do absolutely everything in your computer. even change important system properties that if not tampered corectly with may render your os unusable. 
that's why you get the message to login as root when you do administrative tasks, so you won't allways be the administrator - like in windows - and thus not scrue up your system.

---

### Post by Kobalt on 2007-01-25
Hello,

I suggest you hang around at help.ubuntu.com if you're a beginer in Ubuntu. To learn about root and other permissions stuff, read this doc : 
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/permissions.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/permissions.html)

Cheerio !

---

### Post by jvc26 on 2007-01-25
Take a peek at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) and that may well give you some guidance :)
Il

---

### Post by mangoti on 2007-01-25
> **misfito said:**
> Hello every1 I new at this and I want to know what root is and how to avoid making something bad to my system by installing things as root.


**root** is the super user who has the right to do, see, access and modify anything system-wide on an unix-like system. Critical parts of the system require root privilege to access and modify them. Modifications made by a regular user will not have a system-wide effect  (unless you use "sudo" to gain privileged user rights). That's why it is a good practice to avoid as much as possible using your system as root.

---

### Post by misfito on 2007-01-25
So what you are saying is that is better to use the system as a normal user and not as administrator?

---

### Post by az on 2007-01-25
> **misfito said:**
> So what you are saying is that is better to use the system as a normal user and not as administrator?

Yup.  If you don't want to have to have intimate knowledge of how things work, and just use the software, that's all you have to know on the topic.

---

### Post by Kobalt on 2007-01-25
And by default, Ubuntu doesn't let you start a session as root, you can 'only' use commands as root.

---

### Post by misfito on 2007-01-25
> **Kobalt said:**
> And by default, Ubuntu doesn't let you start a session as root, you can 'only' use commands as root.

And in the case I installed a program that appear to be in root, and I don't know how it finished there, how do I unistall it?

Thanx for the quick response! :)

---

### Post by kosmic on 2007-01-25
Root is GOD and the owner of the Univserse ;)

---

### Post by matt,lng91 on 2007-01-25
does any 1 here use msn messenger if so add me cause i need help    [email]matt.lang91@hotmail.com[/email]

---

### Post by matt,lng91 on 2007-01-25
add me onmsn cause i need help      [email]matt.lang91@hotmail.com[/email]

---

### Post by mykalreborn on 2007-01-25
> add me onmsn cause i need help [email]matt.lang91@hotmail.com[/email]
Reply With Quote 

what kind of help do you need dude? you can allways ask your questions here so everybody can benefit by our answers

---

### Post by irish_flu on 2007-01-25
> **misfito said:**
> And in the case I installed a program that appear to be in root, and I don't know how it finished there, how do I unistall it?

Thanx for the quick response! :)

What did you install, and how did you install it?  Some things (like the Synaptic Package Manager) ask for the "root password" in order to install any software.  that's by design, and is done ot make sure that the person installing the software is the person who runs the machine.

In other words, installing something as root is fine; the point is that you're not doing "everything" (like browsing the web and such) while you're logged in as root (you can't even do this by default with Ubuntu) and you enter the password in order to make system changes (like installing software).

---

### Post by misfito on 2007-01-28
> **irish_flu said:**
> What did you install, and how did you install it?  Some things (like the Synaptic Package Manager) ask for the "root password" in order to install any software.  that's by design, and is done ot make sure that the person installing the software is the person who runs the machine.

In other words, installing something as root is fine; the point is that you're not doing "everything" (like browsing the web and such) while you're logged in as root (you can't even do this by default with Ubuntu) and you enter the password in order to make system changes (like installing software).

I installed wolfenstein ET and it seems that it landed on the root directory, but I don't know how, And to make it worse it doesn't wanna work (the game) right. I've been looking around and found out that is bad to have this program installed as root but I don't know how can I fix this problem.

---

