---
title: "Best way to judge connection status?"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by lucid on 2007-01-01
I have an iburst wireless modem which I've found is easiest configured with pppoeconf. Apparently pon dsl-provider and poff is the way to connect and disconnect (when I don't automatically connect while logging on that is). However, I get 'none so loaded' 'none killed' etc messages which leaves me puzzling if I'm using the commands incorrectly and whether it is a OS issue or an ISP issue. 

The gui has never been of use to me as it never seems to have an effect on connecting/disconnecting and is horribly counter-intuitive. 

Upshot is this: My ISP is down. I want to keep hitting the connect button to see if it is up. On Windows (which I've resorted to) it is really easy. It gives you a clear success or failure message so you know where you are. On Linux I haven't found that. 

Ubuntu likely does have this option and I just haven't discovered how to use it correctly. Any suggestions? :)

---

### Post by seijuro on 2007-01-01
if you're using pon you should be able to check using plog though I'm not sure if pppoe uses pppd or not. I use pon/poff sometimes when my dialup is being flaky to find out of I need to restart the modem driver or not. also you can check to see if you are getting an ip using ifconfig.

---

### Post by MkfIbK7a on 2007-01-01
you could also download wifi radar which has clear error messages as well

---

