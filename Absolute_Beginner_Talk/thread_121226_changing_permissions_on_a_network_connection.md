---
title: "changing permissions on a network connection"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by pompeyjohn on 2006-01-24
Hi there, 

I am confused, and I hope someone can offer some advice. 

Some background first. I have a two machine network. The one I am writing this on is the Ubuntu machine, the other machine is a debian box. I have recently had to rebuild the debian box. 

I used to have a "connect to server" link on my ubuntu desktop which pointed to the debian machine. Once the machine was rebuilt this no longer worked. After a bit of reading around it looked like the best thing to do was to delete the known_hosts file. I have done that.

I have also set up a new connection now. But short-sightedly I set it up for a user, and not for root. I can connect to the machine as *user* using Nautilus.  If I remove that connection and try to create a new connection with the user as root - it just defaults back to the user connection.

When trying to ssh at a terminal line I get the following error:

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX.
Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending key in /root/.ssh/known_hosts:1
RSA host key for 192.168.1.4 has changed and you have requested strict checking.
Host key verification failed.
```

How do I add that key correctly to the known_hosts file. Anyone have a link or tip or example on how it is formatted?

I have added a few scripts to the right click menu in Ubuntu - one of which is Root Nautilus Here. When trying that I get the following error:

Nautilus cannot display "sftp://root@blah blah blah..."

all help very much appreciated :) 

john

---

### Post by pompeyjohn on 2006-01-26
anyone?

---

### Post by rmjokers on 2006-01-26
Have you tried removing the .ssh/known_hosts file for the root user also?  If you do this and try to log in again, it will prompt you that it is adding a new key to the file and then leave you alone in the future.

---

