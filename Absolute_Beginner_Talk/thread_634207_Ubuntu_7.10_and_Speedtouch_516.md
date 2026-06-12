---
title: "Ubuntu 7.10 and Speedtouch 516"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by xuraax on 2007-12-07
Hi,

I have a small network at home built round an Ethernet Speedtouch modem set to always on PPPoE. The network setup on XP is set for static IP's and works well with no problem.

Recently I decided to try out linux so I tried to run Ubuntu 7.10 straight off the CD. No matter what I do I cannot get linux to even see the modem, never mind the internet. Am I missing something?

I have tried to look at similar mails but they all seem to refer to USB modems which is not my case.

Any help or link  would be greatly appreciated.

---

### Post by fineas on 2007-12-07
Not quite sure if it helps, but check here: [http://ubuntuforums.org/showthread.php?t=630424&highlight=sudo+pppoeconf](http://ubuntuforums.org/showthread.php?t=630424&highlight=sudo+pppoeconf)
and here: ([https://help.ubuntu.com/7.10/internet/C/modems-adsl-pppoe.html](https://help.ubuntu.com/7.10/internet/C/modems-adsl-pppoe.html)). The latter can be found under system>help> "connecting to the internet" link> "PPPoE Modems" too.

---

### Post by xuraax on 2007-12-07
I have read the above and the best response I got is when I did "sudo pppoeconf"

system replied " looking for pppoe access concentrator on eth1"

" access concentrator not responding probably due to another running pppoe process controlling the modem"

This other process may be the modem itself which is set up to connect itself to the provider. Any further thoughts?

thanks

---

### Post by xuraax on 2007-12-09
> **fineas said:**
> Not quite sure if it helps, but check here: [http://ubuntuforums.org/showthread.php?t=630424&highlight=sudo+pppoeconf](http://ubuntuforums.org/showthread.php?t=630424&highlight=sudo+pppoeconf)
and here: ([https://help.ubuntu.com/7.10/internet/C/modems-adsl-pppoe.html](https://help.ubuntu.com/7.10/internet/C/modems-adsl-pppoe.html)). The latter can be found under system>help> "connecting to the internet" link> "PPPoE Modems" too.

I have finally got the system to work.

My problem was, I had been following the official instructions as per the second url above. I was doing "sudo pppoeconf" when in fact I should have been doing "sudo pppoeconf eth1" as per the first suggested url above.

Now if somebody can explain why.....

thanks and regards

---

