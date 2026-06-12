---
title: "internet disapeared when i upgraded to Fiesty"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by krull_etc on 2007-04-25
I have an older Dell desktop and used Ubuntu 6.10 for several months.  Tuesday I tried upgrading to 7.04 with a clean install.  It worked fine, but when I turned on my computer Wednesday, my internet connections disappeared.  I can reboot with the old Edgy LiveCD and get online, but can no longer get online using either the Fiesty LiveCD or an install.  I even reinstalled Fiesty to make sure I didn't screw something up.  

I am connecting with DSL.  I can not get online with Firefox, Gaim, or see updates witht he software update tool.  I ran ifconfig on both the Fiesty install and the Edgey LiveCD to compare.  The two are different.  In the non-working Fiesty,  eth0 does not have the inet addr and inet6 addr lines.  It also has a different interupt.

---

### Post by eljalill on 2007-04-25
I am not sure, whether this is your problem, but when I upgraded to Feisty, I had to set up the NetworkManager again, inlcuding changing my /etc/network/interfaces (comment out everything but the lines for lo .... ) . That was for wireless, but maybe, it's the same for cable?

---

### Post by krull_etc on 2007-04-26
That didn't work.  I tried several combinations: commenting everything out but lo, everything but eth1, and everything but lo and eth1.  It didn't make a difference.  (I rebooted after each edit to make sure it wa being read)

---

### Post by Seisen on 2007-04-26
What network card is it?

---

### Post by krull_etc on 2007-04-26
I will have to check the model when I get home. It is the one that came with the computer (a 5 year old Dell desktop).  It did always work fine with Edgy and Fecodra Core 5.

---

