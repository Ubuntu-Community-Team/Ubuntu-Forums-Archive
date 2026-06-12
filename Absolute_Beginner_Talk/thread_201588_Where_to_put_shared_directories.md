---
title: "Where to put shared directories?"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by BCRailrodder on 2006-06-22
Hi,

I am shortly going to be doing a clean install on a new hard drive and since I do not yet have a dedicated file server, I would like to move my collection of music and photos out of my home directory so my family may access them.

I don't imagine that they should go under ./ but I think probably under /usr.  Eventually, I will be setting them up for access from Samba once I get one of my other machines up and running.

Any thoughts, 

Kent

---

### Post by bob7 on 2006-06-22
How about in a folder under /var/? Thats where web pages go. /usr is mostly for program files.

---

### Post by mtron on 2006-06-22
if you want them to show up on your Desktop (with a harddrive icon) mount the new harddrive via fstab to somewhere under /media

i have /media/mp3, /media/video ect.

---

### Post by BCRailrodder on 2006-06-22
[QUOTE=mtron]if you want them to show up on your Desktop (with a harddrive icon) mount the new harddrive via fstab to somewhere under /media

i have /media/mp3, /media/video ect.[/QUOTE]

That's an interesting idea however I am not worried about seeing them on the desktop - I just want to get them out of my /home directory.  

The way I understand permissions to work is that if I close my /home/kent directory to everyone but me (and root, of course) then even if I set permissions for my family to access the /home/kent/music directory, they couldn't get to it.

I would just like to find a safe place in the file hierarcy where they already have access.

Kent

---

