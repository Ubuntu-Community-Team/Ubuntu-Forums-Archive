---
title: "ssh conection refused"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by pref-at-laval on 2007-03-13
I just installed 6.06 and when I try to ssh to it from my Mac i get :"ssh: connect to host 10.0.0.14 port 22: Connection refused". I know that ssh is running because from the Ubuntu machine I can ssh into my Mac. I can also see it in the runnung process's screen.
Do I need to set something for ssh to accept incoming connections.

---

### Post by taurus on 2007-03-13
Doesn't matter if you can ssh to your Mac from your Ubuntu, you need to install sshd, ssh server, on your Ubuntu before you can connect to it from your Mac.  

Use synaptic to install **sshd** on your Ubuntu first then.

---

### Post by pref-at-laval on 2007-03-13
Thanks Taurus. Installed openssh-server with synaptic and it worked first time.

---

