---
title: "Frequency controlling in BSD"
date: 2008-06-24
forum: BSD
---

### Post by cdiem on 2008-06-24
I've understood, that there's no program such as kpowersave for the BSD family (at least I couldn't find one). I'm interested, what way of controlling the powerd do the experienced users of BSD with laptops use? Do you control the processor power schemes in /etc/rc.conf manually, or is there a graphical frontend, which works in a way, similar to kpowersave?

---

### Post by techmarks on 2008-06-24
This is the entry in my rc.conf file

```
# powerd: adaptive speed while on AC power, adaptive while on battery power
powerd_enable="YES"
powerd_flags="-a adaptive -b adaptive" # set CPU frequency
```

---

### Post by cdiem on 2008-09-06
> **techmarks said:**
> This is the entry in my rc.conf file

```
# powerd: adaptive speed while on AC power, adaptive while on battery power
powerd_enable="YES"
powerd_flags="-a adaptive -b adaptive" # set CPU frequency
```

Do you think that my record in /etc/rc.conf would make sense (following down)? Cause since weeks I'm trying to restrict the temperature of FreeBSD on my laptop (it heats up to 70+ degrees Celsium even when doing a simple "pkgdb -F" (I dual boot Debian with cpufrequtils installed, and there are no such problems there)). I'm not quite sure how I should understand the -i and -r flags here:

[PHP]powerd_enable="YES"
powerd_flags="-a adaptive -b adaptive -n adaptive -i 65 -r 45"[/PHP]

This is combined with an entry of [PHP]cpufreq_load="yes"[/PHP] in /boot/loader.conf. 
From the manpage of powerd:
[PHP]-a mode     Selects the mode to use while on AC power.

-b mode     Selects the mode to use while on battery power.

-i percent  Specifies the CPU idle percent level when adaptive mode should begin to degrade performance to save power. The default is 90% or higher.

-r percent  Specifies the CPU idle percent level where adaptive mode should consider the CPU running and increase performance. The default is 65% or lower.[/PHP]

Do you know of anything else, that I should adjust in order to enable frequency scalling on FreeBSD in a way, that my laptop doesn't heat up that much? 

P.S.: I've found just one other useful discussion regarding this, namely [http://forums.pcbsd.org/viewtopic.php?f=6&t=3169&st=0&sk=t&sd=a](http://forums.pcbsd.org/viewtopic.php?f=6&t=3169&st=0&sk=t&sd=a)

P.P.S.: There seems to be another one as well:
[http://209.85.135.104/search?q=cache:thF8oRcPo2wJ:www.bsdforums.org/forums/archive/index.php/t-36491.html+openbsd+cpufreq+powerd&hl=bg&ct=clnk&cd=2&gl=bg](http://209.85.135.104/search?q=cache:thF8oRcPo2wJ:www.bsdforums.org/forums/archive/index.php/t-36491.html+openbsd+cpufreq+powerd&hl=bg&ct=clnk&cd=2&gl=bg)

---

