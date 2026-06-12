---
title: "Strange firestarter activity"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by Klaidas on 2006-10-22
Hello, 

I have recently noticed some strange firestarter activity - I'm not doing anything, but the traffic is about 10kb/s.

Well, I decided to use "Lock" feature - it locks the firewall and no traffic is allowed to get in/out of the computer. However, it still says that the traffic is somewhere about 10kb/s.

Hmm, that's strange. Soo, I disable eth0, but it still shows me traffic usage?!

I curious, what's going on here?...

P.S. Image attached

---

### Post by _duncan_ on 2006-10-22
I'm just guessing... Could it be synaptic or apt-get or aptitude checking for updates in the Ubuntu repository?

---

### Post by Klaidas on 2006-10-22
Well, maybe :| But would it still do it if everything's disabled?

---

### Post by dbott67 on 2006-10-22
Just taking a wild stab here, but it could be local loopback stuff (i.e. traffic on 127.0.0.1).

Try looking at the output of **netstat -a** and look for connections to localhost.  I believe X11 listens on localhost, so it could be related to that... again, just guessing.

-Dave

---

### Post by _duncan_ on 2006-10-22
I'm using dial-up. What I notice with firestarter is after I disconnect, it shows the last activity just before disconnection and stays there. If I reconnect again later, the numbers start to change again.

The main difference between your firestarter screen and mine is I have ppp0 instead of eth0 since we have different connections.

---

