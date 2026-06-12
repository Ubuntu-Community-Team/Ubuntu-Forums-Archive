---
title: "No Permission to enable IP forwarding"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by aozkaya on 2007-09-21
Hi, I need to enable IP forwarding, I have used this command:
sudo echo "1" > /proc/sys/net/ipv4/ip_forward

and I got this error:
/proc/sys/net/ipv4/ip_forward: Permission denied

even I used sudo , why do I have this error? Is there another command that I need to use?

thank you,
aozkaya

---

### Post by Ptero-4 on 2007-09-21
use sudo -s to get a root shell and then do the echo "1" > /proc/sys/net/ipv4/ip_forward command, and then don't forget to close the root shell after you're done with it.

---

