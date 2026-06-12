---
title: "Install p2p"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by Corey4666 on 2006-06-21
hey everyone im new to ubuntu AND linux i never used linux ever till today
i have limewire downloaded for linux and its file extension is .rpm "LimeWireLinux.rpm" and i tryed opening the terminal and typing "sudo alien -i /home/corey4666/Desktop/LimeWireLinux.rpm" and i get this "sudo: alien: command not found" im not sure how to install .rpm's on linux can anyone help me? :confused:

---

### Post by shanepardue on 2006-06-21
there's a limewire clone in the package manager that may suit your needs even better. it's called frostwire, i dig it.

---

### Post by s_h_a_d_o_w_s on 2006-06-21
In the terminal, type: 

sudo apt-get install frostwire

Then reboot.

Applications->Internet->Frostwire

Frostwire looks exactly like limewire, works faster, it's great!

---

### Post by Perfect Storm on 2006-06-21
[QUOTE=Corey4666]hey everyone im new to ubuntu AND linux i never used linux ever till today
i have limewire downloaded for linux and its file extension is .rpm "LimeWireLinux.rpm" and i tryed opening the terminal and typing "sudo alien -i /home/corey4666/Desktop/LimeWireLinux.rpm" and i get this "sudo: alien: command not found" im not sure how to install .rpm's on linux can anyone help me? :confused:[/QUOTE]

You need the alien application first.

```
sudo apt-get install alien
```

---

### Post by Corey4666 on 2006-06-21
thanks very much! for the replys O:) 

but i have a problem still

============================
corey4666@corey4666-desktop:~$ sudo apt-get install frostwire
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package frostwire
corey4666@corey4666-desktop:~$
============================

i would like to say ubuntu is a great os! im enjoying learning :mrgreen:



EDIT: sorry i didnt see someones reply

corey4666@corey4666-desktop:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package alien
corey4666@corey4666-desktop:~$

another problem

---

### Post by Perfect Storm on 2006-06-21
How's your sourcelist looks like?

```
nano /etc/apt/sources.list
```

---

### Post by s_h_a_d_o_w_s on 2006-06-21
Check out my Howto. It will show you how to enable extra repositories (What you don't have, it's basically access to more programs, such as frostwire) and how to get frostwire. It also shows you how to get JAVA, if you want it.


:-)
[URL="http://www.ubuntuforums.org/showthread.php?t=176442"]
Here[/URL]

---

### Post by Corey4666 on 2006-06-22
thanks everyone i figured it out just wanted to let you know and btw i had to install xubuntu i was having problems with booting up ubuntu so i just switched

---

