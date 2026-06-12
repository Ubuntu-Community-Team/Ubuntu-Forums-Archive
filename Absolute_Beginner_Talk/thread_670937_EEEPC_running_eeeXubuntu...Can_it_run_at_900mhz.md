---
title: "EEEPC running eeeXubuntu...Can it run at 900mhz?"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by nycityguy on 2008-01-18
I am sure everyone knows that eeepc is advertised as a 900mhz system, ut my 4g only rn at 630mhz. Is there a idiot proof way of making the system speed up?

---

### Post by jordanmthomas on 2008-01-18
```
cpufreq-selector -g performance
```
should do it.  It will stay this way until you reboot.  If you want a permanent solution, this can be done as well.

If it says you must be root to do it, prepend a sudo (seems to vary from distro to distro whether or not you need one)
```
sudo cpufreq-selector -g performance
```

However, the processor should scale up as needed so the fact that it's only running at 630 MHz just means your processor doesn't have a need to be running fast at the moment (saves power)

---

### Post by nycityguy on 2008-01-18
thanks for the qick response; however, it says no cpufreq support when I use that command

---

### Post by jordanmthomas on 2008-01-18
Hmm, after a quick googling it seems perhaps Samsung underclocked the frontside bus from 100 MHz to 70 MHz?  I'll look more into it later, but the difference in 600 MHz and 900 MHz isn't really THAT great.

The processor itself IS a 900 MHz processor, but since the FSB is only 70 MHz, 70 * 9 = 630.  Had they left it at 100 MHz, 100 * 9 = 900.  I'm sure altering anything to get the FSB back up to speed would break your warranty.

---

### Post by markp1989 on 2008-01-18
[http://code.google.com/p/eee-ubuntu-support/](http://code.google.com/p/eee-ubuntu-support/) 

if you install that, then press fn +f6 it enables over clocking , then if you press fn +f6 again it makes it go back to normal speed

---

### Post by gn2 on 2008-01-18
If you run it at 900mhz will the battery run flat quicker?

630mhz and 512mb RAM should be plenty, my laptop's an old 500mhz P3 with 192mhz RAM and it runs Xubuntu just fine.

---

### Post by jordanmthomas on 2008-01-18
My laptop's actually got pretty similar specs (if you consider it in scaled-down mode, which it usually is).
It's got a 1.5 GHz processor but it's almost always scaled down to 600 MHz and it's plenty fast.  I do turn the scaling off when I go to play games, but I don't think anyone gets an EEEPC for games.

---

