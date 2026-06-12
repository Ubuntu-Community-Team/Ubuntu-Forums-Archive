---
title: "internet speed"
date: 2005-07-24
forum: Absolute Beginner Talk
---

### Post by Strongbad on 2005-07-24
How do I check my internet connection speed? It seem's like it's going a little slow.

-Strongbad-

---

### Post by adwait on 2005-07-24
Try
[http://www.dslreports.com](http://www.dslreports.com)
[http://www.bandwidthplace.com/speedtest/](http://www.bandwidthplace.com/speedtest/)

---

### Post by Strongbad on 2005-07-24
It tested at a whopping 16.3 kbps!  ](*,)
That could explain why it seemed slow.

Anyone know how I can speed it up a bit?
My windows machine tested at 41 kbps

-Strongbad-

---

### Post by byen on 2005-07-25
wow..i tried the test it too and my 4-6mbps broadband seems to give me 324.1 kilobits per second while it gave me a consistent 2.5mb/ps on XP... someone know anything about this?

PS- strongbad...sorry to walk-in on yur Question like this bro...just had to vent out a bit here...

---

### Post by poofyhairguy on 2005-07-25
Are yall using wireless? Many Linux wireless drivers are slower than the windows counterparts.

---

### Post by Strongbad on 2005-07-25
No, i'm just using a phone cord.

-Strongbad-

---

### Post by Strongbad on 2005-07-25
My modem is set to port /dev/ttyS14/ (why I don't know...) could that possibly be slowing it down? And if so, is it possible to switch it to a more typical port?

-Strongbad-

---

### Post by adwait on 2005-07-25
You could try turning off ipv6........dont remember how.......

---

### Post by byen on 2005-07-25
[QUOTE=poofyhairguy]Are yall using wireless? Many Linux wireless drivers are slower than the windows counterparts.[/QUOTE]
 yup! gotta say the diff is frustating! well... cant have it all i guess :-(

---

### Post by Strongbad on 2005-07-25
Does anyone know how to turn off ipv6?

-Strongbad-

---

### Post by damonw5 on 2005-07-25
[QUOTE=Strongbad]Does anyone know how to turn off ipv6?

-Strongbad-[/QUOTE]
 In firefox, in the address bar, type "about:config" (without quotes). Then search for ipv6. There should be a value that is set to "true". Set it to "false".

---

### Post by polo_step on 2005-07-25
[QUOTE=Strongbad]How do I check my internet connection speed?[/QUOTE]
This is the best list, by location, and will save you from having to dig around on the site to find it:

[http://www.dslreports.com/stest?more=1](http://www.dslreports.com/stest?more=1)

Funny, but my DSL link on the Linux box is slightly slower than on the XP box.  Not drastically, but consistently.

---

### Post by majikstreet on 2005-07-25
[QUOTE=damonw5]In firefox, in the address bar, type "about:config" (without quotes). Then search for ipv6. There should be a value that is set to "true". Set it to "false".[/QUOTE]


thanks for the tip :)

---

### Post by porsher_puddles on 2005-07-25
i have the same problem on my dial up mine is so slow i couldn't even do the bandwidth test it timed out. i have tried every suggestion and thing i can think of i am useing ubuntu warty, i will be upgrading to hoary when the cd's arrive which could  be quite sometime.

In the mean time i would like to know how to upgrade my modem drivers to see if thats the problem. this is what i get when i  query the modem in windows

Q0V1E0 - OK
AT+GMM - COMMAND NOT SUPPORTED
AT+FCLASS=? - 0,1,1.0
AT#CLS=? - 0,1,8
AT+GCI? - COMMAND NOT SUPPORTED
AT+GCI=? - COMMAND NOT SUPPORTED
ATI1 - 255
ATI2 - OK
ATI3 - V1.200-K56_DLS
ATI4 - 56000bps Voice Modem For Australia
ATI5 - 022
ATI6 - RCV56DPF L8570A Rev 45.0/45.0
ATI7 - 000

---

### Post by Strongbad on 2005-07-26
Ok, now it's up to 26.8 kbps, but that's still pretty slow! Any more suggestions? They are most welcome!

-Strongbad-

---

### Post by poofyhairguy on 2005-07-26
[QUOTE=Strongbad]Ok, now it's up to 26.8 kbps, but that's still pretty slow! Any more suggestions? They are most welcome!

-Strongbad-[/QUOTE]

Sure. here are ways to make firefox feel faster:

[http://www.ubuntuforums.org/showthread.php?t=38646](http://www.ubuntuforums.org/showthread.php?t=38646)

Block some adds, tweak the firefox and it will be as good as dial up browsing can get.

---

### Post by Strongbad on 2005-07-26
Thanks for all your help!

-Strongbad-

---

### Post by mingus on 2005-08-13
Try your speed test with another browser to see if there is any signif diff compared to Firefox.  

Be cautious with the speed tests.  For example, the dslreports test offers the choice of several different servers which will give different results, which is a function of nbr of hops and latency.  Some online tests are actually "through put" tests, which would include page rendering, you don't want that.

---

