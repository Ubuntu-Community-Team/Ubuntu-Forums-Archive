---
title: "[SOLVED] Failed to Initize HAL!"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-03-19
Upon restarting, i got the message "failed to initilize HAL"! I changed the conncurent value from i think "none to yes"using this gude: [http://www.xlntsolution.com/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/](http://www.xlntsolution.com/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/)  and now i cant get on the internet cause my network was disabled..Stupid I know...cause i didnt see it was for Fiesty until I changed it

How botched am i?  The network starts functionally with my desktop, just cant get online cause my network died (i assume a result of the change I made)..Any Ideas?:

---

### Post by Oldsoldier2003 on 2008-03-19
> **sox fan Matt said:**
> Upon restarting, i got the message "failed to initilize HAL"! I changed the conncurent value from i think "none to yes"using this gude: [http://www.xlntsolution.com/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/](http://www.xlntsolution.com/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/)  and now i cant get on the internet cause my network was disabled..Stupid I know...cause i didnt see it was for Fiesty until I changed it

How botched am i?  The network starts functionally with my desktop, just cant get online cause my network died (i assume a result of the change I made)..Any Ideas?:

try ```
sudo /etc/init.d/networking restart
```

---

### Post by sports fan Matt on 2008-03-19
ok..i have to run upstairs to make the change and will see what occurs..It may take me a few minutes to get back upstairs

---

### Post by sports fan Matt on 2008-03-19
it seems to restart it, but upon relog in i get the same behaviour...I also got a whole ton of couldnt update errors when I tried a sudo-apt-get update to see if that was the issue :(:(

---

### Post by sports fan Matt on 2008-03-19
and it still says "network disabled" even when I try and enable the network...

---

### Post by ag65151 on 2008-03-19
I am having the same problem. I am able to get my network back by issuing 

```
sudo /etc/init.d/hal start
```

My network comes up a couple of minutes after hal starts.

But I am unsure what I did that made this error start.

---

### Post by sports fan Matt on 2008-03-19
in my case..i flipped to faster boot the shells i assume from concurrency=shell to concurrency=none and vice versa..i'll try this and see if it works..wish me luck~!

---

### Post by sports fan Matt on 2008-03-19
All fixed..you all are lifesavers!

---

