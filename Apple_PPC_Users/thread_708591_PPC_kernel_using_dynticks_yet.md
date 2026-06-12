---
title: "PPC kernel using dynticks yet?"
date: 2008-02-26
forum: Apple PPC Users
---

### Post by stream303 on 2008-02-26
I just did a quick check of my standard Gutsy kernel to see my kernel timer freq:

```
grep CONFIG_HZ /boot/config-`uname -r`
```

and saw that I'm running at 250 hz.  (I checked Debian Lenny and it was the same)

I was thinking about compiling my own kernel at 1000 hz for a low-latency desktop, but does dynticks itself take care of that?

My other concern about compiling my own kernel was when I read in this article on 2.6.21 about issues with the low-quality capacitors that surfaced in recent years, so maybe keeping my hz low, or using dynticks is the safest bet in the long run:

[http://kernelnewbies.org/Linux_2_6_21](http://kernelnewbies.org/Linux_2_6_21)

I've read about some G5 iMac owners having failing capacitors, so maybe a low-latency desktop might not be a good idea. :(

The usual tricks of trying to change the kernel freq via /etc/sysctl.conf don't seem to apply anymore since the rtc module isn't even loaded, and wasn't even available to modprobe when I tried!

Update: I guess I should have read further that PPC support for dyntics is in 2.6.24.  But the question is, will Ubuntu use it in PPC and how can we check for it?

---

