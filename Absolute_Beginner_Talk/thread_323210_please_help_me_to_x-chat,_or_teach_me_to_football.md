---
title: "please help me to x-chat, or teach me to football"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by monk_rock on 2006-12-21
I installed ubuntu this morning. so i am as new as you get. I was hoping someone could guide me to an appropriate x-chat file to install. I've installed a few programs today, succesfully i might add, but i can't seem to find an x-chat program made for ubuntu.](*,)

---

### Post by BarfBag on 2006-12-21
Just fire up Terminal (Applications, Accessories, Terminal) and type:

> sudo aptitude install xchat

---

### Post by PriceChild on 2006-12-21
Or, a nicer looking version:
```
sudo aptitude install xchat-gnome
```This version looks nicer but has a lot of advanced options missing... I've only started needing them when opping a channel though.

---

### Post by monk_rock on 2006-12-21
I don't know what you made me do, but this happened
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find package "xchat".  However, the following
packages contain "xchat" in their name:
  xchat-gnome
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

I'm guessing it didn't work or something like that

thank you very much for trying though.

---

### Post by monk_rock on 2006-12-21
sudo aptitude install xchat-gnome worked great, but does anyone have the heart to explain to me what i just did. i think i understand the install command, but what was the "sudo aptitude" was the program already on the system or did i go get it somehow?:-k

---

### Post by scrooge_74 on 2006-12-21
> **monk_rock said:**
> sudo aptitude install xchat-gnome worked great, but does anyone have the heart to explain to me what i just did. i think i understand the install command, but what was the "sudo aptitude" was the program already on the system or did i go get it somehow?:-k

When installing from command line you have to use "sudo" to have root user powers

you can update your system doing "sudo apt-get update" and then "sudo apt-get upgrade"

Apt is going to become your best friend, it does the same things as synaptic but from the command line

---

### Post by riven0 on 2006-12-21
> **scrooge_74 said:**
> When installing from command line you have to use "sudo" to have root user powers

you can update your system doing "sudo apt-get update" and then "sudo apt-get upgrade"

Apt is going to become your best friend, it does the same things as synaptic but from the command line

And aptitude! Don't forget about aptitude. :)

---

