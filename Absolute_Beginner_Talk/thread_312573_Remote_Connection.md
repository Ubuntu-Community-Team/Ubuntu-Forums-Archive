---
title: "Remote Connection"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by matthewinuk on 2006-12-04
How can I set up my ubuntu thing so that I can connect to my machine over the internet using "putty". I have never used remote connections before so a step by step guide, or a link to one would be very very useful to me. Thankyou in advance.

:)

---

### Post by matthewinuk on 2006-12-04
anyone??!

---

### Post by dann0 on 2006-12-04
Here is how I did:
First, install OpenSSH-server on your ubuntu: sudo apt-get install ssh
Then if you have a firewall, you need to open up a port for it. (default is 22), an direct incoming trafic to yor server.
I guess you want to connect from a Windows-machine, using Putty.
Connect to your public IP-adress from Putty.
You may want to set putty to use the UTF-8 encoding, otherwise the special chars wont work.
(At least that's my experience, I'm using Swedish keyboard).

---

