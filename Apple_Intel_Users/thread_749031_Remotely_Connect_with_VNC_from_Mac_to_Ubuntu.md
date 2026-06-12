---
title: "Remotely Connect with VNC from Mac to Ubuntu"
date: 2008-04-08
forum: Apple Intel Users
---

### Post by boozker on 2008-04-08
I know there are a couple threads on how to do this, but I am having problems because they are either oriented for connecting on a local network (which I can do fine) or they are focused on Windows and SSH and Putty. 

The problem I have is I want to be able to work with my Ubuntu OS at home while at work. I want to use some of the applications, so I don't want to connect with Terminal an grab files.

My biggest problem is how to I get my external IP and open it up for certain connections. Can I ONLY allow my Mac's IP? I have 10.5 by the way. I really like working on my Ubuntu OS, for all of my web programming with Geany and Filezilla and how it looks and feels.

Can someone just point me in the right direction. I am having no luck with Google or the suggested topics it gave me.

---

### Post by wblancqu on 2008-04-08
You could try "Hamachi" to create a virtual LAN over WAN. It's fairly easy and has versions for every OS. Then you can VPN connect as if the computer was in your local network (by using the hamachi given IP).

Grtz

---

### Post by cyberdork33 on 2008-04-08
VNC is not very secure in itself especially with a port open to the internet. This is why most tunnel through SSH (which is quite secure). There is really nothing special to do on the Mac side. 

You have to open a port to the internet to allow access. This is dependent on your home setup... do you have a router? firewall? 

then you can install ssh on your Ubuntu machine, and connect an ssh session by issuing a command in the OSX terminal:
```
[FONT=Arial,Helvetica,sans-serif]ssh2 -L yy:localhost:xx ubuntuusername@ubuntuip[/FONT]
```[FONT=Arial,Helvetica,sans-serif] This will setup a connection that passes information on your local machine (the Mac) on port yy to the remote machine (Ubuntu) on port yy.

So as an example for a VNC session running on the Ubuntu machine on port 5200 (not open to the internet) I could issue the command:
[/FONT]```
[FONT=Arial,Helvetica,sans-serif]ssh2 -L 4400:localhost:5200 ubuntuusername@ubuntuip[/FONT]
```[FONT=Arial,Helvetica,sans-serif] and then I could use my VNC client to connect to localhost::4400 and this connection request is forwarded over the ssh connection (which is all encrypted) to the remote computer.

I recommend JollysFastVNC for your Mac client.

Reference:
[http://www.ssh.com/support/documentation/online/ssh/adminguide/32/Port_Forwarding.html](http://www.ssh.com/support/documentation/online/ssh/adminguide/32/Port_Forwarding.html)
[/FONT]

---

