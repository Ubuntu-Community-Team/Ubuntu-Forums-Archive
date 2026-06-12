---
title: "Telnet connection"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2007-02-05
I am trying to connect from my XP machine to my Ubuntu desktop via telnet port 23. It gives me th login details, but keeps saying login failed even after I put my details in.

I have read some guides but can't work it out at all. Is there something I need to do to login via telnet?

---

### Post by Ryan450 on 2007-02-05
telnet ewww ewww ewww..

on your local network sure its fine as nobody else sees it, but if your going to login remotely like that may as well give yourself internet capabilities safely as well. 

I say ditch telnet and forget about it, then go install OpenSSH from synaptic. This will allow you to login into your ubuntu machine with your regular user and password. As for the client on windows, go download a copy of putty and use that. ssh uses encryption, so its perfectly safe to use across the net as well.

---

### Post by lamego on 2007-02-05
You should install the openssh server and connect from Windows using putty, it is safer because unlike with telnet your data will be encrypted.

---

### Post by Bagboy23 on 2007-02-05
Heh, stupid telnet. 

Openssh it is. Thanks guys.

---

### Post by punx45 on 2007-02-05
ssh is way cooler than telnet anyway.  with one protocol (and thus one open port) you can have the shell, file transfers with SFTP, and forward ports to another machine outside your network.  

i use SSH port forwarding to access Mythweb away from home on my MythTV machine that is not public.

---

### Post by steve.horsley on 2007-02-05
Aside from the advice to use SSH instead, no, there's no spacial requriement for logging in, and you should be able to use the same username and password. I can't imagine why you would have trouble logging in with telnet, provided your username and passeord don't have any odd characters that the two machines treat differently. The same would be true for SSH.

---

