---
title: "loging into server from vista"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by amstern on 2007-12-25
I am brand new to Linux.  I am trying to set up a file and print server to use with a windows network.  I installed Ubuntu gusty server and the xubuntu gui.  I have samba running and can access my windows vista computer from the server.  I can see the server on the vista machine but can´t log in.  I have tried setting up a user on the server to log into but can get it to work.  Machines are connected through a D-Link router.  I gave the server a static ip.  Do I need to set up a static IP on each windows machine? I not sure how.

Any help would be appreciated.  Its taken me three days to get to this point.

---

### Post by frup on 2007-12-25
a regular user or a samba user?

you might need to open terminal and type

smbpasswd user -a (i think that is the syntax)

and then provide a password. and you mean just for file sharing right? Otherwise you might prefer to use ssh.

---

### Post by amstern on 2007-12-25
I don´t know enough to answer the question.  My goal was to use the lunix machine to store documents and music that I could access from the windows machine.  I have both Samba and SSH installed but am accessing the system mostly through the xbuntu gui.

---

### Post by frup on 2007-12-25
Well when you try to connect from Vista it is asking you for a username and password?
If the user you created isn't working type

sudo smbpasswd -a newuser in terminal

That will allow you to add a new samba user and define their password. Try using that then to log in from vista.


You also need to declare folders as shared, with correct permissions...

---

