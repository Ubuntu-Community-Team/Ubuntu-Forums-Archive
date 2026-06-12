---
title: "What happened to my connection?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Brucey on 2007-05-12
Last night I was browsing the internet just fine.  Then I wake up this morning and all of the sudden, no internet.  My brother and I are on a D-Link DI-614+ router connected to a DSL modem.  His computer is running Windows XP and its working fine, as I'm posting from it right now.  But whenever I try to browse with Firefox on my ubuntu computer, it always says "server not found".

Can anyone help me out?

---

### Post by Acksys on 2007-05-12
See if running ```
sudo ifdown -a
``` and then ```
sudo ifup -a
``` fixes this. Also make sure all cables are connected securely and all that.

If you're still having problems, please post the output from ```
ifconfig
``` and ```
dmesg | grep eth
```

---

