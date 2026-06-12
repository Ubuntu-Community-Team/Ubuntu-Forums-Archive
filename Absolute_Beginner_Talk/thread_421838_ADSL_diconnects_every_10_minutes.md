---
title: "ADSL diconnects every 10 minutes"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by yigals on 2007-04-24
I had the same problem in Edgy and I thought it will come to an end with Feisty, but it didn't.

The Internet disconnects with no reason every ten minutes, there isn't any indication for this, simply Firefox is failing to load any more pages and any download get stuck.

I use DSL connection through 10/100 Regular network plug.

---

### Post by Alekc on 2007-04-24
if you are still connected but unable to open any page it can be dns issue. Try to use dns servers from OpenDns (208.67.222.222 and 208.67.220.220).

When you are disconnected what does ifconfig say?

---

### Post by yigals on 2007-04-24
How do i change my dns?

---

### Post by yigals on 2007-04-25
My ifconfig after disconnection:
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:84.228.94.194  P-t-P:213.8.255.155  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:3813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3760389 (3.5 MiB)  TX bytes:784021 (765.6 KiB)

---

### Post by Alekc on 2007-04-25
For dns change: System->Administration->Network->Dns->add

---

### Post by yigals on 2007-04-25
So far looks good with the DNS change :) this almost drove me crazy,

Thanks !!

---

### Post by aquaeyed on 2007-04-25
i had the same problems but i turn off the 2monitor sign on fiesty near the clock, and it no more disconecteted again =)

---

### Post by yigals on 2007-04-26
Oops :(

Seems like I was happy too soon. I'm still having the same problem as before, even with the DNS change.

aquaeyed  :
How did you disable this 2 monitors icon?

---

### Post by Seisen on 2007-04-26
Are you running a modem>router>computer or modem>computer? Is the modem connected to the computer or does it go from the modem to a router than to the computer.

---

### Post by yigals on 2007-04-26
from an ADSL modem straight to the computer

---

### Post by yigals on 2007-04-28
Anyone? Please? This is the only reason I'm still using my crappy XP, you would understand..

---

### Post by kelvin spratt on 2007-04-28
i know this does not help but i had the same probllem in xp when i bought a new router well a bit worse every 20 mins computer rebooted thats why i tried linux never had the problem since isent life strange

---

### Post by yigals on 2007-04-28
If it helps to solve the problem, I have to do:
sudo poff -a
and wait a few seconds before I type:
sudo pon dsl-provider
to restore the connection

---

