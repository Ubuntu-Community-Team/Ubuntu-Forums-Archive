---
title: "network setup"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by tbrooke on 2008-01-28
I have a windows network setup at home with samba and it works ok but I don't need to connect to my windows computer very often. I have also setup nfs and vnc but I have to use the server's IP address and when I look at network places my server doesn't show up

How do I get my server to show up? Do I need to set up DNS?

Tom

---

### Post by Joeb454 on 2008-01-28
Is the server running Windows or Ubuntu? If its a Windows server, then you need to connect using RDP

---

### Post by bcrom on 2008-01-28
Can you access the windows box by typing the IP address into nautilus file browser?  If so, I recommend you just bookmark the location and not worry about finding it in Network Places.

---

### Post by tbrooke on 2008-01-28
The server is running Ubuntu - I will rarely if ever need to contact the windows computer since I transfered all my file to the Ubuntu server. I basically want a Ubuntu network with the option of sending a file to my windows machine if needed

Tom

---

### Post by bcrom on 2008-01-28
Hmm.  I recommend using a ubuntu network and configuring your windows box for regular windows sharing.  If you ever need to access the windows box, use SAMBA.

---

