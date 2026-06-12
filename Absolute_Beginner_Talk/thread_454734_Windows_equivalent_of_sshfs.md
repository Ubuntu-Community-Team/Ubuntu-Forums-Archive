---
title: "Windows equivalent of sshfs"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by docshawnc on 2007-05-25
Hi - I'm able to use sshfs to access my server (feisty) over the internet from my laptop (feisty) just fine.  I can also use putty from my office windows box to give me a terminal session on my server.  I was wondering if there is a windows client/program which will allow me to graphically link to the folders on my server from my windows box.  All suggestions greatly appreciated and have a wonderful weekend.

---

### Post by Mazen on 2007-05-25
can you give an explanation on how to ssh to your own pc?
i mean how to get ur ip and all that? i already had a post, and as for windows i think it has a default program which is Remote Desktop Access or something as such, and i think VNC works on Windows too

---

### Post by docshawnc on 2007-05-25
What I am looking for is not a VNC/RDP type of connection, but a windows based program of sorts that will connect via sshfs to a Feisty server.  That way I could be looking at my desktop on my windows machine, click a folder and open a folder on my Ubuntu server.  That is what I'm after- hope this helps

---

### Post by Mazen on 2007-05-25
well, the way i've seen it work , u can do the same with VNC by installing the server on ur Fiesty and a viewer on ur windows, but since you do not want this type of connections i don't think it would do the thing.
i'm still looking for a howto to do that so "technically" i'm not ur best help just giving it a shot!

---

### Post by Znupi on 2007-05-25
[www.winscp.net](www.winscp.net)
I use it all the time.

---

### Post by docshawnc on 2007-05-25
perfect -thanks!

---

### Post by qpieus on 2007-05-25
> **Mazen said:**
> can you give an explanation on how to ssh to your own pc?
i mean how to get ur ip and all that? i already had a post, and as for windows i think it has a default program which is Remote Desktop Access or something as such, and i think VNC works on Windows too

This is a little off-topic, but since you asked....

You need to use a dynamic DNS service. This service ties your (periodically) changing IP address (assigned by your internet provider) to a static name of your choosing. For example, you could choose the name mazen.homedns.org and the DNS service will assign that name to your IP address. To connect into your pc remotely, you use mazen.homedns.org as the address rather than the actual IP. There are programs you can set up to automatically notify the dynamic DNS provider when your IP address changes so that your static name will always be linked to your IP. Here's some documentation on dynamic DNS:

[https://help.ubuntu.com/community/DynamicDNS]("https://help.ubuntu.com/community/DynamicDNS")

---

