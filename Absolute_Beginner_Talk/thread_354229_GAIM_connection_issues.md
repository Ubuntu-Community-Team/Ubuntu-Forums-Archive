---
title: "GAIM connection issues"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Azdak on 2007-02-05
So I'm running a fresh install of 6.10 and here is my issue.

Every time i make an attempt to log on to an AOL/ICQ account using Gaim it simply refuses to connect.  I have done a fair bit of searching on this issue and the consensus seems to be the default ipv6 support is to blame.  This is further backed up by the fact that i was having connection probs with firefox until I disabled ipv6 in about:config.

So great, fantastic, I have figured out the problem.  I also found a few fixes......

which failed to work (or which i failed to execute properly)

So here I am, starting from scratch: Gaim still wont connect...hence my making this thread.   If i have missed some blatently obvious stickied thread, then I apologize for wasting your time, guys, but I'm pretty damned stumped at this point.

---

### Post by ComplexNumber on 2007-02-05
are you using any firewall frontend such as firestarter? i'm wondering if you've made your firewall quite strict so that it may be blocking the port that gaim connects  on aol.

---

### Post by Azdak on 2007-02-05
i've got it going through port 5190, which is what all the other computers on my network are using to connect to AIM, and they have no problems

---

### Post by ComplexNumber on 2007-02-05
> **Azdak said:**
> i've got it going through port 5190, which is what all the other computers on my network are using to connect to AIM, and they have no problems
yes, but you can finetune how your computer connects to the router. i'm just wondering if you have your firewall set too stringently.

---

### Post by Azdak on 2007-02-05
ok, well if that's the case i know it's not longer an ubuntu issue...but if you have any ideas as to how to diagnose it i would be very appreciative.

---

### Post by ComplexNumber on 2007-02-05
> **Azdak said:**
> ok, well if that's the case i know it's not longer an ubuntu issue...but if you have any ideas as to how to diagnose it i would be very appreciative.
so have you previously installed firestarter? and did you change any settings in it?

---

### Post by Azdak on 2007-02-05
im behind a dsl modem with a built in hardware firewall...my roomie and are are screwing with it right now

---

### Post by ComplexNumber on 2007-02-05
> **Azdak said:**
> im behind a dsl modem with a built in hardware firewall...my roomie and are are screwing with it right now
a router is a hardware firewall. i guess if it works for the other computers then it isn't anything with the router. i just wondered if you'd played about with the settings on your own (software) firewall that was causing gaim to refuse the connection. you can always do some pinging using network-tools.

---

### Post by Azdak on 2007-02-05
I wasn't aware that there was a software firewall that came with ubuntu...how can i access its settings?

---

### Post by ComplexNumber on 2007-02-05
> **Azdak said:**
> I wasn't aware that there was a software firewall that came with ubuntu...how can i access its settings?
the actual firewall is called iptables. i've never tried to alter the settings on the command line, but i do have firestarter installed, and thats a frontend for iptables so that you can  change the settings.

---

### Post by irish_flu on 2007-02-05
Did you already follow instructions like these, to turn off IPV6 completely?

[http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)

---

