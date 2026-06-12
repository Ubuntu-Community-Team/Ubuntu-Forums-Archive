---
title: "ssh from ubuntu to ubuntu"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by hfnd on 2008-04-13
How can I terminal into my Ubuntu server from my Ubuntu laptop like I Putty into my server from windoze machine?

---

### Post by spydon on 2008-04-13
> **hfnd said:**
> How can I terminal into my Ubuntu server from my Ubuntu laptop like I Putty into my server from windoze machine?

ssh username@ip
Or if you use dyndns or something just ssh username@dyndns
If you have the same username on the two computers you dont have to write "username".

---

### Post by jcwmoore on 2008-04-13
your client will need openssh-client, and the server will need openssh-server installed.  It sounds like you already have the server set up, so install the client part to you client machine and then run ssh as suggested above

---

### Post by spydon on 2008-04-13
> **jcwmoore said:**
> your client will need openssh-client, and the server will need openssh-server installed.  It sounds like you already have the server set up, so install the client part to you client machine and then run ssh as suggested above
I think the openssh-client is installed by default on Ubuntu so that shouldn't be a problem. :)

---

### Post by hfnd on 2008-04-13
Thanks,

Open ssh client is installed, but when I try to a access a terminal on my server from a web browser I get my web launchpad.

---

### Post by spydon on 2008-05-05
How were you supposed to get a terminal in a browser? :S

---

### Post by graben3 on 2008-05-05
Personnaly I only use SSH to connect to a remote DB so gSTM is the perfect app for me : it setup my ssh tunnel and connects to it. then I use mysql administrator to manage DB on the server.

it works great. also as said before ssh username@server/ip works well too

---

