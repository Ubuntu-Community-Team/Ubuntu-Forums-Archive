---
title: "Updated and Ubuntu doesnt work."
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by h4m574h on 2006-12-15
Hello again!

I am running Ubuntu Edgy as my only OS. Last night Ubuntu prompted me for updates, and I updated the system, but planned to restart later. About 10mins after that, there was an electricity shortage and the computer shut down *the hard way*. I tought it-s not a big deal when I was waiting for the computer to restart. Ubuntu booted normaly, but then when it reached about 3 bars it froze. Also the hard-disk stopped working. I tried it a few times, but I got the same results every time.

Does anybody know what do do?


-h4m574h

---

### Post by Bachstelze on 2006-12-15
Can you still boot in recovery mode ? If so, try running

```
apt-get -f install
```

---

### Post by John E on 2006-12-15
This sounds very similar to what I just experienced (except I didn't get any power outage!)

---

### Post by h4m574h on 2006-12-15
I tried recovery mode. It boots, but stalls when it reaches
```
[17179608.164000] eth0 no IPv6 routers present
```


I get the same sydroms as before. It doesnt really make sense, cause if there was no IPv6 router present, I would probably get the same error on Live too.




EDIT> added IPv6 to blacklist. Hopefuly it will work. (it doesnt work =(((((( - maybe IPv6 isnt the problem after all.....)

---

### Post by John E on 2006-12-15
Did you make a backup copy before updating?

---

### Post by igknighted on 2006-12-15
Can you do a disk error check?  The power outage might have messed up your disk with the hard shutdown, you should rule that out first.

---

### Post by h4m574h on 2006-12-15
Em...a very wierd question, but I-m kinda green.....where do I find this this error check. Memcheck is only for memory, right?

---

### Post by saxsux on 2006-12-15
I got the same problem on my laptop (no hard restart though).

After a couple of hard restarts when booting froze, it seems to be running alright.

I use ndiswrapper for my wireless card, and booting tends to be slow on the "Configuring Network Interfaces" stage. Could that have been anything to do with it?

---

