---
title: "Restrict User Access"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by OMRebel on 2006-07-27
How can I lock down Ubuntu to where a user has very limited access.  For instance, if I have a user that I only want to have access to Firefox, and the Applications menu, how would I do that?

---

### Post by MaximB on 2006-07-27
> **OMRebel said:**
> How can I lock down Ubuntu to where a user has very limited access.  For instance, if I have a user that I only want to have access to Firefox, and the Applications menu, how would I do that?

system>administration>users and groups
create a new user ,then>properties>user privileges tab
and have some fun playing with it

if you want to restrict access to a folder or a file
folder>properties>premissions>select a group and set a premission.

---

### Post by OMRebel on 2006-07-27
Thanks for your quick reply.  I have created a user, and uncheck everything in the User Priviledges tab.  However, how could I start going about taking away access to:

Places -> Network Servers
Places -> Connect to Server

System -> Preferences -> ALL
System -> Administration -> ALL

I have looked around, and can't get that part figured out.

---

### Post by MaximB on 2006-07-27
uncheck the privilege "Excecuting system administration tasks"
(and by the way - if anyone wants to go to administartin> - he will need a password by default).

---

### Post by OMRebel on 2006-07-27
Thanks.  I think what I may have to do is to go with KDE and their kiosk program.  With Gnome, after trying those things, the user was still able to browse the network. :o(

---

