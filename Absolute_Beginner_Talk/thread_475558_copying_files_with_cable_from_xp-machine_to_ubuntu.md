---
title: "copying files with cable from xp-machine to ubuntu"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-06-16
Hello,

I want to copy very large files from my neighbour's computer (windows XP) to my laptop - Ubuntu 7.04. I got a cable, which can connect these two computers' USB ports. What should I do after that? How can I access "My Documents" folder of this alien XP-machine with my Ubuntu laptop? Any ideas?

---

### Post by FleetAdmiral74 on 2007-06-16
How big of a file are we talking about?

---

### Post by O-pos on 2007-06-16
some over-2-GB sized files. totally 12 GB

---

### Post by FleetAdmiral74 on 2007-06-16
Well I am not sure about a usb cable, but if you just put em on the same network (I think you have to install something called samba), you should be able to read the ntfs and just copy the files from there.

---

### Post by carloslosgrande on 2007-06-16
Surely a usb cable connection would look like a usb flash drive to ubuntu? in effect? And I can read windows files from usb flash without any problems.
I'd just try it before loading samba and trying to set up a network connection.

---

### Post by O-pos on 2007-06-16
> **carloslosgrande said:**
> 
I'd just try it before loading samba and trying to set up a network connection.

What are these network connections to be set up?

---

### Post by bigken on 2007-06-16
if you have a router just hook both pc to it via ethernet cable run the network wizzard in windows to share files and folders

on the linux pc in a terminal type 

sudo aptitude install samba

sudo smbpasswd -e (your name)

sudo smbpasswd -a (your name)

hey ho your networked

---

### Post by bigken on 2007-06-16
ps there is another way ehternet crossover cable still run all the wizzards and installs 

but manually asign the ip address subnet mask and dns

---

### Post by Austin_KW on 2007-06-16
If this is a once off copy of a lot of data, then for speed it is difficult to beat temporarily moving the disk to the new machine. Sometimes the sneaker-net works best.

---

### Post by insane_alien on 2007-06-16
sneakernet: never underestimate the bandwidth of a truck full of hardrives hurtling down the highway.

*note: update from tapes so it keeps up with the times.

---

### Post by O-pos on 2007-06-16
I think I will try with samba. I hope it's not difficult to set up windows' networking tool

---

### Post by Austin_KW on 2007-06-16
You should not need any setup to be a client for the XP machine. Just go to places->network->windows network

---

### Post by normworthy on 2007-06-16
this is what I was trying to do when I messed up my machine.

from Ubuntu I could access the shared folder on the Windows machine, but I could not access the Ubuntu machine form windows. 

Will what you have described let me access a folder from widows on the ubuntu machine?

Thanks Norm

---

