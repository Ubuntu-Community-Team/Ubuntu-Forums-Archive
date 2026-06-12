---
title: "Roaming profiles"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by pboekelman on 2005-10-20
Hi,

I want to use ubuntu as a server, and let ubuntu clients connect to it.
But as I have several user accounts and several client pc's I am wondering if there is a way to let the user get the same environment on any pc.

So the desktop background, mappings and so on? 

In a ubuntu PDC server and MS Windows client situation it is possible and known, but in a ubuntu-ubuntu situation?

---

### Post by tvds on 2007-05-16
Yes I also would like to know if there is a thing like Roaming Profiles in Ubuntu.
Please let us know !

---

### Post by gerdt on 2007-05-17
I'm also looking for a similar situation:

One Ubuntu server, with roaming profile etc., user management etc.
Multiple Windows and Linux (Ubuntu) computers, logging on through the server.

---

### Post by tvds on 2007-05-18
Well, I also posted this question on a dutch forum.
And... it aint very easy.
[http://forum.ubuntu-nl.org/message/106265](http://forum.ubuntu-nl.org/message/106265)

---

### Post by Rich78 on 2007-10-22
Did anyone ever get this working?

---

### Post by hyper_ch on 2007-10-22
That should work with a thin client setup... basically you are booting all the data from the server in your client.

---

### Post by Bytor on 2007-10-23
How about just using NFS to share /home from the server, place a line in /etc/exports on th server like this:

/home           192.168.0.0/16(rw,sync,root_squash) 172.31.0.0/16(rw,sync,root_squash)

and a line in the clients' /etc/fstab like this:

fileserver:/home /home nfs     rw,nodev            0       0

And voila - when you log in on any workstation on your network you hav ethe same home drive and thus the same settings fro gnome, kde, etc...


Of course, this means emptying out the local /home dir

---

