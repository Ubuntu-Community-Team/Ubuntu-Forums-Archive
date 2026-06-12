---
title: "Networking issues"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by mattdwilnew on 2007-02-14
Hey all, Chapter 4 in the Ubuntu vs Me saga.

I have got a RAID with the programs that we have for our business on it. We all (5-7) run a program from the RAID drives that we need for our business. Now at first I just had everyone logging in from their windows machines into my network user account on linux. It was going well but wanted to avoid conflicts etc, I set everyone up with their own network username and password on the server and set it up in the windows machines. It ran well! Until I found out every time we saved a file/edited a file it would change ownership of that file to the user and noone else could access it! (Everyone was in the same user group).
So i changed it back to everyone on my user account. Now using the program we are having problems accessing files (we are all trying to access the same files - for example there is a log which everytime anyone does something it adds it to the log - but we are all using the program and thus adding stuff to the log at the same time.)

Getting frustrated, I don't care about who on my network accesses the files. Can I set the share up to be accessed and edited, deleted, saved, whatever by anyone on the network? Google is just useless, too many help questions on different topics.

---

### Post by whistlingtony on 2007-02-15
Err.... More info please!

I take it you are sharing your files via Samba? Care to post your smb.conf file?

---

