---
title: "Problems accessing an OS X folder over network"
date: 2009-06-23
forum: Apple Hardware Users
---

### Post by dominion_vortar on 2009-06-23
Good Afternoon,

I have a macbook and a mac mini both on the same wireless network. I use Ubuntu a lot on the mini for various things. I want to transfer a folder across my network to my mini (OS X 10.5.7 to Ubuntu 9.04). 

I can see the drive ("Leopard"), and type in my password for the OS X user when prompted, and can browse most files, however, when I try to access "Downloads" inside my user folder, I get the error 'You do not have the permissions necessary to view the contents of "Downloads"' 

How can I get round this please? Any help is appreciated.

Thanks very much for your time,
John. :KS

---

### Post by nathanid95 on 2009-12-05
If you use [Samba]("http://www.samba.org") in Ubuntu you should be able to access those files from a Mac the same way you access Windows files on a network.

---

### Post by linuxopjemac on 2009-12-06
you could also put that stuff in the shared folder in OSX, I guess that such a folder gives all the rights to other users. or you could simply chmod -R 777 folder to give all users access (dangerous though).

---

