---
title: "Securing Remote Desktop"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by william_hunter on 2007-04-27
I have set up remote desktop for a game server I am running on my Ubuntu machine, and I want to make sure the people I give access to the server can only access a certain executable and one other directory. (the executable is called nwnstartup.sh and the directory is called Server Vault, in case you need that info)

I suspect what I need to do is set up an account for the people I want on he machine, right? Give that a password, and then they will be able to access the box. The thing I dont get is exactly how to limit the access to other places on the server. I guess what I need is a handholder to show me...lol

---

### Post by wormser on 2007-04-27
I would recommend tunneling the remote desktop connection threw ssh.  The first step would be to set up the user account.  I am not sure how you would restrict them, somebody else will have to help you there.  

Then connect via a ssh tunnel.

```
ssh -L xxxx:localhost:yyyy username@ipaddress
```

The L switch binds a remote port to your localhost port.  
xxxx is the local port on your machine
yyyy is the remote port
ip address can be replaced with the domain

---

### Post by william_hunter on 2007-04-27
I should add that I am running this server behind a hardware firewall, and have the firewall on the machine disabled at present. I can give people access as it is now, using VNCViewer, but I need to secure the files. Can I just modify permissions on stuff?

---

### Post by wormser on 2007-04-27
I also forgot to add this.  To connect via vncviewer use: localhost:xxxx as the address.

---

