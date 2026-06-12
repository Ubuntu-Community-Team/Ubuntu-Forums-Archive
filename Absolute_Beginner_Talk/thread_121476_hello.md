---
title: "hello"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by zoran on 2006-01-25
hello everybody,:p 
please, step by step, how to install any new program from CD/DVD, using Synaptec.(or somethig elese)Use 5.10!
I am total beginner,

---

### Post by chimera on 2006-01-25
Synaptic is used to download and install packages from the internet, not from a removable media(such as CD/DVD/flash)

To install something, just open Synaptic (System->Administration->Synaptic package manager, you'll need to enter your user password you created when you installed Ubuntu), and find it(press the search button) for example if you know the name of the program, just enter it, but if you're looking for an mp3 player, type "mp3 player" and have it search in name and description.

---

### Post by Stealth on 2006-01-25
Or if you downloaded some deb packages from somewhere and burned them on CD you can:

1. Copy files to your home folder (Places -> Home)
2. Open terminal (Programs -> Accessories -> Terminal)
3. Type: *sudo dpkg -i nameofdebpackage.deb*

The only thing is that it won't automatically resolve any dependency problems like if you were to do it in Synaptic. Though it does name the files incase you wanna go dependency-hunting, but check if the package is in Synaptic first! :D

---

### Post by zoran on 2006-01-25
hvala,
I will try!

---

### Post by zoran on 2006-01-25
hvala,
I will try!

---

