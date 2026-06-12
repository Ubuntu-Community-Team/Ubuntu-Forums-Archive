---
title: "How can I get picasa to see my network drive?"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by brachiopod on 2006-12-28
Hi, sorry, bit of a Linux beginner here.

I have all my photos on a network drive (running linux, Samba server). The drive appears on my desktop "places" and I can view it there, but I don't know how to get Ubuntu/Picasa to see the drive, it only seems to seem my physical drives. Does this have something to do with what file manager Picasa is using?  Obviously this is something that a Linux person would laugh at :)  but I could use a pointer, Thanks!

---

### Post by brachiopod on 2006-12-31
Maybe I wasn't clear, or maybe this can't be done.

I want to access a network drive from Picasa. The drive is something like smb://dsm-g600/hdda
The drive shows in my desktop "places".   
I tried creating a symbolic link to smb://dsm-g600/hdda, but that did not appear to work. 
Is there any way to make this drive show in the picasa folders list?
Thanks!

---

### Post by brachiopod on 2007-01-03
Solved, this thread shows what to do to get the network drive mounted as a directory, then Picasa can see it. The only difference was that I didn't get a desktop icon by doing this, but the folder did appear.

[http://www.ubuntuforums.org/showthread.php?t=327930](http://www.ubuntuforums.org/showthread.php?t=327930)

---

### Post by Jussi01 on 2007-01-03
Got a feeling the desktop icon comes only when you mount in fstab - thats what I did, and it came :)

---

