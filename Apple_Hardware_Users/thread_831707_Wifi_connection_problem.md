---
title: "Wifi connection problem"
date: 2008-06-17
forum: Apple Hardware Users
---

### Post by Zaff on 2008-06-17
Hi all,
My macbook's hard drive died on me the other day and I was using gutsy and it was working perfectly, wifi and all. Now I have installed hardy on my newly repaired macbook and installed the madwifi drivers using the script on this post : 
[http://ubuntuforums.org/showthread.php?t=798485](http://ubuntuforums.org/showthread.php?t=798485)
I did that because it just didn't seem to work when I tried to do it manually.

Now this works very well at home on my personal Wifi. I'll add that I have another laptop (Toshiba) with the same setup and the wifi works too at home.

But here (work) none of them will connect to the wifi. The wifi connection here is through a 128bit ASCII pass. I also tried converting it to Hex and it won't work either. it just keeps trying to connect and then after a few minutes pops the "Wireless Network Key Required" dialog again.
Is there something I'm missing here ? should I change something ?
Thanks

---

### Post by phidia on 2008-06-17
What does > lshw -C network output?

That should give something to work with. 
The output of sudo iwconfig may be useful too.

---

