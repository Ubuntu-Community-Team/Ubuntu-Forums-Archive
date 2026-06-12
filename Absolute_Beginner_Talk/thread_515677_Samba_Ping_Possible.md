---
title: "Samba Ping Possible?"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by nickburns on 2007-08-02
I have a raid storage ubuntu box running at home with samba on it.  I gave it a static IP number and I can get to the shared folders through the "Connect to Server" by using the server name.  The problem is I want to ssh into the box and cannot get the name to resolve.  I don't remembe r the static IP (and am too lazy to plug a monitor into the box).  Is it possible to find the IP number through smb?  Why does it connect though the "Connect to Server" and "Network Browser" but I cannot ping it?

---

### Post by guilly on 2007-08-02
if you do a ping <hostname> in a terminal window, it should say something like reply with the address of that box.

---

### Post by nickburns on 2007-08-02
'no route to host' is all I get.

---

### Post by NuK on 2007-08-02
If you have VNC enabled in the server, you won't need a monitor to see what happens there... it's a good practice, specialy for home servers.

---

### Post by guilly on 2007-08-02
I say just hook up the damn monitor :)!!

how about going into your routers firmware? usually thers an ip table in there somewhere

---

