---
title: "SSH reveals linux version"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Wardazo on 2007-03-14
Hi

I just did a scan on my server with nmap (nmap -v -A xxx.xxx.com) and it revealed my linux version via the ssh server:

22/tcp open ssh OpenSSH 4.2p.1 Debian Ubuntu3.1

How do I stop the ssh server from revealing my linux version.

On second thoughts Ubuntu3.1... no it's not. Now I'm really confued.

I know it's a good idea to turn off apache broadcasting too much about itself and linux. Does the same follow for the ssh server.

Any help would be very welcome.

Ward

---

### Post by finer recliner on 2007-03-15
this is half a guess, but assuming your server is running sshd, check where the banner option is pointing in /etc/ssh/sshd_config. by default it points to /etc/issue.net

this file (issue.net) is displayed everytime a user logs on to your server. i've changed mine, so i dont know what it says by default (maybe some info about what OS your running perhaps?)

check it out, its a starting spot.

---

