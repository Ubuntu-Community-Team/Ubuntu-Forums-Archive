---
title: "[SOLVED] Realtek 8139 problems in Ubuntu Studio"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by brightscreamer on 2007-11-04
Alright...I tried the fix in this thread:

[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

No dice. I installed Ubuntu Studio (the latest ver.) on my cousin's PC yesterday. While I was installing it, I received a message saying something to the effect of "unable to detect internet/HTTP settings." I thought...oh well, I'll fix it when I boot into Ubuntu. How wrong I was! I was able to locate the NIC in the device manager, but I can't connect to the internet for anything! I am typing this from my laptop. Does anyone have any ideas on how to fix this?

---

### Post by brightscreamer on 2007-11-04
I forgot to mention I am not dual-booting Windows...I installed Studio over everything.

---

### Post by brightscreamer on 2007-11-04
Did I not include enough information? :(

My poor cousin can't use the internet! Someone please save him!

---

### Post by brightscreamer on 2007-11-04
Did I perhaps post this in the wrong section of the forum? Can anyone steer me in the right direction? Even a hint?

---

### Post by brightscreamer on 2007-11-05
O.k., I feel pathetic now. I'm begging you! Please help me!

---

### Post by brightscreamer on 2007-11-07
I know I'm not the only one with these issues...I can't be. Am I the only one here? Can anyone hear me?

---

### Post by braedsjaa on 2007-11-07
> **brightscreamer said:**
> Alright...I tried the fix in this thread:
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)
No dice. I installed Ubuntu Studio (the latest ver.) on my cousin's PC yesterday. While I was installing it, I received a message saying something to the effect of "unable to detect internet/HTTP settings." 
... 

That thread is specifically for dual-booting with windows, the problem being with a windoze update which knobbles the 8139 NIC. So this *won't* fix your problem.

You should post a new question with more details - 
Do you know when or where the message comes from? 
Do you know for sure it is a problem with the 8139 NIC? 
Are your internet/HTTP settings correct?  -  check System> Administration> Network. 
Does the network  (eg. the router/modem/firewall) restrict access in any way which may need some re-configuring?

---

### Post by brightscreamer on 2007-11-07
Do you know when or where the message comes from?

It popped up during the text install.


Do you know for sure it is a problem with the 8139 NIC?

I would assume so. The internet works when the modem is hard-wired to my laptop, but not when it is hard-wired to my cousin's desktop.


Are your internet/HTTP settings correct? - check System> Administration> Network.

It is set automatically.


Does the network (eg. the router/modem/firewall) restrict access in any way which may need some re-configuring?

Don't think so. It works fine when connected to my laptop, which is running the same version of Ubuntu Studio.

FWIW, I did a checksum and it came out fine. Also checked the disc for errors and found none.

---

### Post by brightscreamer on 2007-11-07
Nevermind. I just re-installed it with the ethernet cord plugged in and it recognized everything fine. Great success!

---

