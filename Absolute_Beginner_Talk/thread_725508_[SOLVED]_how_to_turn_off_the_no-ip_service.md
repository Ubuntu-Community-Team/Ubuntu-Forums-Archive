---
title: "[SOLVED] how to turn off the no-ip service"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Meph1st0 on 2008-03-15
I have a Dynamic DNS client called No-IP running on my server at home.  I need to change its configuration file found in /etc/no-ip.conf  but when I go in there it's all giberish.  The command I used when I setup the service was Sudo no-ip -C  But when I enter that command I get an error saying:

 Configuration file '/etc/no-ip.conf' is in use by process 5149. ending!

How do I either kill the no-ip process or turn off the process so that I can reconfigure it?  anybody know?

I'm about 5 thousand miles away from the server so I have to do it via the command line through ssh or I can use vnc to get to the gui if need be.

---

### Post by Meph1st0 on 2008-03-15
nevermind, I figured it out.

sudo no-ip -K 5149

kills the process

then I reran it to reconfigure it.

---

