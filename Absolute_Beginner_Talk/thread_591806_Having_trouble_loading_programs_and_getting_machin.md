---
title: "Having trouble loading programs and getting machines to see each other"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by turbobill on 2007-10-25
I need to get Ubuntu client talking to Ubuntu server and XP client talking to Ubuntu server.  

Also, having trouble installing PostgreSQL 8.2.5 on Ubuntu Server.

The only PostgreSQL I can find is for Fedora or RedHat and they seem to be version 7.?.? ... 

Also, the Ubuntu package is 7 something but I need to install 8.2.5 on the server.

And, when trying to open an *.rpm i get something like: "don't know how to open this ... "

Total noob here, please forgive total noobness.

Thanks for any help,
Wm

---

### Post by turbobill on 2007-10-25
Server is 6.06.1 with GUI installed over it, the U client is Dapper.  

Running on home LAN( not wireless ).

---

### Post by llamakc on 2007-10-25
You could build postgresql from source if you have certain version needs, or upgrade the O/S to a version of Ubuntu that has the version you need already packaged. Gutsy has 8.2.5-1.1 by the way.

While some rpm's CAN be installed via alien, I recommend you do not use that method and either upgrade or build it from source. Upgrading the server may be easier after all is said and done.

What do you mean by "talking to" one another? Can you ping one machine from the other one? What is the end goal that you have in mind? Specifics help.

---

### Post by turbobill on 2007-10-25
Yeah, sorry for the vagueness.

The idea is to set up Ubuntu server running PgSQL to serve up data for an app I'm writing for a small mfg. firm.  Their clients are all XP boxes but we like the idea of a linux server, for several reasons.

I can access files on the XP box from the U server, but can not access the server files from the XP box.

Thanks for the response.
Wm

---

### Post by llamakc on 2007-10-25
Have you installed samba yet? Set up any shared folders?

---

