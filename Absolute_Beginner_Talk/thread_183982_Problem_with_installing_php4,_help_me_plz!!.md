---
title: "Problem with installing php4, help me plz!!"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by cpthk on 2006-05-29
Problem with installing php4, help me plz!!

I have searched the forum, I knew this page tells me how to install php4:
[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

I did command: sudo aptitude install php4

but it tells me couldn't find any package ehose name or discription match "php4"
.....

I also tried apt-get, problem still exist.
they also removed lots of packages like flex

What should I do?

---

### Post by Noelinho on 2006-05-29
At a guess, you probably don't have the universe repositories enabled.

Go to System --> Administration --> Synaptic Package Manager. Then select Settings --> Repositories. Are all the boxes ticked, and so they include 'Community Maintained (Universe)'? If they don't, tick the box and click 'reload' to refresh the repositories.

Then search for php4 in synaptic, or shut down synaptic and go back to the terminal and try to install from there again.

---

### Post by sudomania4 on 2006-05-29
Which version of Ubuntu do you have installed? Dapper or Breezy? Open a terminal, type ```
lsb_release -a
```and hit Enter. If the output of that command says something about Ubuntu 6.06 Dapper LTS, you are running Dapper. If the output of that command says something about Ubuntu 5.10 Breezy, you are running Breezy. Now that you know your version, you can enable the universe repository. Type ```
sudo gedit /etc/apt/sources.list
``` into the terminal. A window should come up with a text editor and file. Add this line to the bottom of that file IF YOU ARE RUNNING DAPPER: ```
 deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
``` Add this line to the bottom of that file IF YOU ARE RUNNING BREEZY: ```
 deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
```Save the file by clicking "Save", then close the window. Now, in the terminal, type ```
sudo apt-get update
``` and then try to follow the directions on that site.

---

### Post by Noelinho on 2006-05-29
Since you're probably a new user, I should point out that those aren't contradictory methods, they do the same thing. They're just different ways of doing it.

---

