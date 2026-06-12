---
title: "need CPU details"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by Samurai Penguin on 2008-04-03
I tried System > Preferences > Hardware Information but it doesn't give any
details about my CPU, just the brand / speed

I would like to find out if my Intel is a Northwood or Prescott. How do I do this? Thanks

---

### Post by Bachstelze on 2008-04-03
You usually can deduce that from the frequency, amount of cache and supported extensions. Else, you'll have to open the case.

Please paste the output of

```
cat /proc/cpuinfo
```

---

### Post by Samurai Penguin on 2008-04-03
thankyou

---

### Post by m60dude5 on 2008-04-03
One other thing you can do is click System, Administration, System Monitor, and click the System Tab and it will tell you all the information about the cpu, memory, system, etc.

---

