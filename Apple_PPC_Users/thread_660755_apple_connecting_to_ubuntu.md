---
title: "apple connecting to ubuntu"
date: 2008-01-07
forum: Apple PPC Users
---

### Post by strip21 on 2008-01-07
This is going to sound like im mad. but anyway here it gose.

I have been given the task to install Ubuntu 7.10 server, and get all the clients to connect to it. This i have done. The problem i have is that there is a apple mac that for some reason can not connect to the server it can see it but not log on to it. 

I'm running samba server and i think this is what the mac is seeing. Under the windows client i can set the log in details to the work group, pc name and domain settings (no PDC installed). Is this the same for mac, as in i need to find out what the pc name work group the mac is in or is there something i need to setup on the server? 


Any comments please. By the way i don't know anything about apple software or how they work.

---

### Post by Knightwise on 2008-01-08
Hey,

You're doing it about right, The one thing you need to do to connect to the linux machine is in the finder click on " GO " , "Connect to server " and then enter smb:\\IP.OF.YOUR.SERVER/SHARENAME Then osx will prompt you for the login and password to connect to the share and then you're good to go.

happy networking.:popcorn:

---

