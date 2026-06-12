---
title: "ssh tunneling"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Nxion on 2008-02-20
Hi,

When I used windows I had setup with putty a secure ssh tunnel so I can use Remote Desktop Connection to my windows machine over ssh. How would I go about setting that up on Ubuntu ?

Thanks

---

### Post by timbounceback on 2008-02-20
see [here]("http://ubuntuforums.org/showthread.php?t=702711")

---

### Post by dannyboy79 on 2008-02-20
> **Nxion said:**
> Hi,

When I used windows I had setup with putty a secure ssh tunnel so I can use Remote Desktop Connection to my windows machine over ssh. How would I go about setting that up on Ubuntu ?

Thanks

could you be more specific? which machine will you be sitting at? which machine will have the ssh server running on it. 

I myself only have 1 open port on my router to inside my network, which is keypair ssh server. I use puttygen to convert the ssh server keyfile to something putty can use, then I setup my tunnels for x11vnc (port 5900) and also a dynamic link to can browse sites that my work blocks, then after I ssh into my homme ubuntu machine, I then can fire up IE or Firefox, tell it to use the socksv5 proxy 127.0.0.1 port 8080 (that's what I tunneled) and I am all good on the browsing. or I fire up tightvncviewer and connect to localhost:0 and I am vnc'd into my home x11vnc server. This will only work if you have an X session already running however. good luck

---

### Post by Nxion on 2008-02-20
I will be sitting at the linux machine. I am never physically at the windows machine.

---

### Post by Nxion on 2008-02-20
> **timbounceback said:**
> see [here]("http://ubuntuforums.org/showthread.php?t=702711")

Why did you link me to a post on unistalling programs ???

---

