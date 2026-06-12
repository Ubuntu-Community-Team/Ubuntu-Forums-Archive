---
title: "Configuring Terminal Server Client--works on XP"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by sammermpc on 2006-12-06
I've always had windows remote desktop working from my laptop (on windows xp pro) to my desktop at home (also on windows xp pro).  I know that you can use Terminal Server Client to do the same from Ubuntu, but no matter how I try to configure it, I get a "error: unable to resolve host".

When I am in windows (even a friends laptop, that I just used), all I need to do is type my hostname (mysupercomp), and everything else works like magic.  Now that I am using Ubuntu, how do I configure terminal server client to allow me to log into my windows xp screen?

---

### Post by pavel_kbc on 2006-12-06
did you installed ssh server ?

sudo apt-get install ssh

---

### Post by sammermpc on 2006-12-06
Thanks--I did as you suggested and installed shh.  Unfortunately, I'm having the same problem as before--I think it might be as simple as I simply do not know what to put into the fields: Domain, Client Hostname, ect.

---

### Post by Cderugg on 2006-12-14
Try putting the IP address in instead.

---

### Post by gigaferz on 2006-12-15
I use at work treminal server client to log into  a windows server at the main office.

Just type the IP address.. and go to the performance tab, hopefully you can have a good speed.

---

### Post by FastZ on 2006-12-15
What do you put for Protocol, the User name, Password, Domain, Client Host name fields?  I know the Computer field will have the remote IP address for the computer you are trying to get into, but what goes in the other fields?  I'm trying to terminal into my Ubuntu Edgy Server machine and I have SSH Server installed on both as well as the SSH client.  What do I need to do?

---

