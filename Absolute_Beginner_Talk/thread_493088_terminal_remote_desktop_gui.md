---
title: "terminal remote desktop gui"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by gigaferz on 2007-07-05
Hello

In ubuntu I go to internet, terminal services and enter the company server ip to connect to it.

My ubuntu was acting up,so I installed fluxbuntu, the problem here is that I have to connect to the server to work on their system and I have to do it via terminal "sudo rdesktop"

but i would like to have the gui that exists in ubuntu , to especify rdp,size,and some performance options..

wich package do i need to install?

emergency ,please??

Is ubuntu 6.06

---

### Post by tronica on 2007-07-05
I think i understand your question correctly; the terminal server client app in gnome has those options.  Just click the different tabs at the top and then save it.

---

### Post by gigaferz on 2007-07-05
I am using Fluxbuntu, and rdesktop  does NOT have a graphical interface for fluxbuntu.

I am using it right now via command line.

I would like to install the terminal server client (i mean the graphical interface) that is in gnome.so i can use the options  that I need.

---

### Post by tronica on 2007-07-05
In that case just do 

> sudo apt-get install tsclient

then to launch it just type tsclient from a terminal

---

### Post by gigaferz on 2007-07-05
thank you it works pretty good!!

---

