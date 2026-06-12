---
title: "ADSL won't start"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by yigals on 2007-02-08
Feb  8 12:42:26 yigal-laptop pppd[5189]: Timeout waiting for PADS packets
Feb  8 12:42:26 yigal-laptop pppd[5609]: Timeout waiting for PADS packets
Feb  8 12:42:27 yigal-laptop pppd[5189]: Unable to complete PPPoE Discovery
Feb  8 12:42:27 yigal-laptop pppd[5609]: Unable to complete PPPoE Discovery

This is the plog output

---

### Post by shareMenaPeace on 2007-02-08
Hi, 
did it worked before?
Did you used pppoeconf to configure the pppoe?

What modem you have? USB? Wireless? Cable?

---

### Post by yigals on 2007-02-09
It's been working once before, on a live CD, than I installed and never got it started again, I've ran 'pppoeconf', and it seems to be ok, also I couldn't trigger the connection only by 'pon dsl-provider' and had to start 'pppoeconf' every time i tried to connect.

---

### Post by Michal77 on 2007-02-19
Hi,
I have similar problem on my friend laptop. It works on Cd-live and during first session after restart of computer i got the same feedback like you. The same ADSL router works fine with my laptop.
Any one any idea what's wrong?
M.

---

### Post by zvacet on 2007-02-20
Make sure that you have all repositories open.If you do make conection as you did before qand go to [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29")
Replace Exec=gksudo /opt/rp-pppoe-3.8/go-gui with Exec=gksudo tkpppoe

---

