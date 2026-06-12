---
title: "apt-get NOT getting in 8.04 on PPC xserve"
date: 2008-05-11
forum: Apple Hardware Users
---

### Post by docfx on 2008-05-11
I posted earlier requesting advice re: setting up 7.04 server w/ LVM on a PPC G5 Xserve. With only one response, I thought I should try to download 8.04 server iso and do a fresh install (no data at this point to be concerned about). 

I did a guided LVM install which seemed to complete. I've configured it as DNS, LAMP, OpenSSH servers.

However, the first step I wanted to do post install was to get/install the 'joe' editor. I did 'apt-get install joe', but only rec'vd the following error:

> Reading package lists....Done
Building Dependency Tree
Reading stat information....Done
E: Couldn't find package joe

Which is odd, in that the previous 7.04 install didn't have a problem finding 'joe'

---

### Post by docfx on 2008-05-11
Nevermind! I'm a bonehead! I configured everything EXCEPT the network (my phat fingers must've selected don't configure). 

When I looked at /etc/apt/sources.list, the ports were correct, but it had commented out the security ports because it couldn't resolve. I tried the get aptitude update and it also couldn't resolve the ports... 

Problem was self-inflicted.

Hardy 8.04 w/ LVM as DNS, LAMP, MAIL and OPENSSH successfuly installed on G5 PPC Xserve. Editor 'Joe' installed. 

Now to go format Drive 2 and prep for client sites.

---

### Post by stream303 on 2008-05-12
Glad to hear that is resolved.  I'm interested to see how well that xserve holds up for you in a server environment with Hardy.

---

