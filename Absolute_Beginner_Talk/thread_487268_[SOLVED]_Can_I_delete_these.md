---
title: "[SOLVED] Can I delete these?"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by DrMilo on 2007-06-28
I have a bit of a fetish with getting the Internet to run as fast as possible. I noticed a number of items under networking/hosts that appear to be ipv6 related. I have already disabled ipv6 in Firefox and blacklisted it in Ubuntu but it seems that someone is determined to load it! Am I wrong? Is this not something to do with ipv6? Will it harm anything if I delete these? One more thing, is there some trick to getting rid of these like the blacklist for it in Ubuntu. I have included a screenshot of the offending hosts. Thanks in advance!

---

### Post by milton1 on 2007-06-28
Those are the reserved ipv6 hosts (loopback, broadcast, etc.). They shouldn't be slowing you down at all. However, if you absolutely must, deleting them should not do you harm, assuming you are using strictly ipv4 on you network.

---

### Post by DrMilo on 2007-06-28
Sounds good, I'll leave them alone then. After the ordeal (to me) of getting rid of ipv6 in the first place I'm being a little vindictive towards it!

---

### Post by alienexplorers on 2007-06-28
if you go in your /etc/modprobe.d/blacklist you can add this line to disable ipv6.

> blacklist ipv6


---

### Post by Detonate on 2007-06-28
In my hosts file, I did not delete them, but I have them all commented out.

---

### Post by DrMilo on 2007-12-12
> **Detonate said:**
> In my hosts file, I did not delete them, but I have them all commented out.

Thanks, I'll do it that way.

---

