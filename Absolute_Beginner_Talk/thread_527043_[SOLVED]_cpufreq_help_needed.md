---
title: "[SOLVED] cpufreq help needed"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-08-16
I want to use cpufreq because I am sick of hearing my laptops fan running all of the time.

If I do:
```
 sudo cpufreq-selector -g ondemand

```

I get
```
 No cpufreq support

```

How can I make it work?

---

### Post by overdrank on 2007-08-16
> **fuzzyhair said:**
> I want to use cpufreq because I am sick of hearing my laptops fan running all of the time.

If I do:
```
 sudo cpufreq-selector -g ondemand

```

I get
```
 No cpufreq support

```

How can I make it work?

Hello again, if you are speaking of the acer laptop that is strange because this one runs as a whisper, but that goes to show you the difference between computers. If you go to synaptic manager and search for cpu there is a lot of info on apps that maybe can help. Good luck!

---

### Post by Bachstelze on 2007-08-16
```
cpufreq-info
```

What gives ?

---

### Post by yorkie on 2007-08-16
this will probaly help you its quick+easy and it works the part you need is near the bottom but read all of it

[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

---

### Post by tdrusk on 2007-08-16
> **HymnToLife said:**
> ```
cpufreq-info
```

What gives ?

It first told me to install it. I thought it was already installed, but w/e. I installed it and now I get
```

tyler@tyler-laptop:~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU

```

---

### Post by examancer on 2007-10-21
I have a very similar laptop... Acer Aspire 3620 w/ Celeron 1.5M, 512MB RAM, 80GB HDD, DVD+/-RW, etc..

By default Ubuntu does not recognize that my cpu supports scaling. The following guide helped me right away... the key is the p4_clockmod module, probing it and adding it to /etc/modules...

[http://www.howtoforge.com/cpu_frequency_scaling_ubuntu](http://www.howtoforge.com/cpu_frequency_scaling_ubuntu)

Hope that solves your problem. I know it solved mine :)

---

