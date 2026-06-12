---
title: "[SOLVED] SO Fed Up with Busy Host!"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by coldstatue on 2007-09-08
I have a desktop, my wife has a laptop. Both are running Feisty.
We used to have an NFS share, with me as the host. I also have a printer physically connected to my comp. Printer sharing and NFS worked flawlessly. After several changes over time, (changing home directory to own partition, updates, and many other things) NFS and the printer sharing stopped working. I'm not sure what caused it.

I tried starting over with NFS, via
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

I have also used the official docs for the printer sharing. 

My wife can't mount my share drive or use my printer. In both cases, she gets a busy host error.

I can mount her share just fine though. We can share this way, but my comp is the one that is always on, not hers, so it causes problems. She cannot print to my printer.

We can ping each other all the time. 

I have checked both of our settings dozens of times, and all that are mentioned in the official guides are correct. 

SO... I figure there is some setting on my computer that is blocking her from connecting to my box. We both have static IPs, and like I say, all settings mentioned in the NFS (client and server) as well as printer sharing (client and server) guides are correct. I installed firestarter at some point, but it is off.

Where else should I be looking? Both NFS and printer sharing were extremely easy to set up the first time, so I know I am missing something outside of the files and settings mentioned in the guides.

What could it be?

I will post any outputs requested.

Thanks for any help.

I would humbly request that anyone who is experiencing the same issue subscribe to this thread, rather than reply, as the people who can help us are more likely to hit the unanswered posts. Thank you.

---

### Post by coldstatue on 2007-09-08
Solved. Even when firestarter doesn't show in session apps, and is not in the systray, it can be running.

---

### Post by robert_pectol on 2007-09-08
To verify that your firewall is indeed off, do, "sudo iptables -L -nv" at the command prompt.  You should get something resembling the following:
```

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

```
If your default policies are anything but, 'ACCEPT', or you have any other rules listed, then your firewall is still enabled.

---

### Post by coldstatue on 2007-09-08
Thank you, but I would like to use it.

I just needed to add my wife's IP to the policy - allow connections from:

I am so ashamed. please do not throw fruit.

Thanks for your time.

---

### Post by robert_pectol on 2007-09-08
> **coldstatue said:**
> Thank you, but I would like to use it...
Understood.  I just wanted to give you a way to verify things during your troubleshooting.
> **coldstatue said:**
> I am so ashamed. please do not throw fruit.
No sweat!  If this is the extent of your Linux woes, I'd say you're in good shape!  :-)

Anyway, take care.

---

### Post by coldstatue on 2007-09-08
no seriously, this boggled me for 2 MONTHS!!!! Man, I just can't believe that firewall didn't cross my mind. What's the first thing you ask a person who has network issues? (once you're sure everything's plugged in.) hmph!


This is not the extent of my linux woes, I assure you. ;0) I am learning, thanks to this forum and the good people who inhabit it. 

That was a big one though.

I am so happy.

Thanks again, and have a good one.

---

