---
title: "confused about getting NEWEST versions?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by kamathews on 2007-09-09
First Some Background - I'm new to Linux (played with Unix decades ago - stuck with M$Windows in corporate America since....)

Running Ubuntu (6.06 Dapper Drake) on an old PIII box with minimal resources...
    {education is better than gathering dust}

Trying to install ClamAV.  First attempt worked fine through Synaptic. It installed v 0.88

Tried to Refresh the data files and got complaints that I need v 0.91

so..... I've tried to start using command line:
      sudo apt-get install <pkg-name>

dependancies track down to libc6... reports it needs >=2.3.6-6
   I have  2.3.6-0ubuntu20.5 installed.

Trying:
   sudo apt-get install libc6

simply reports "nothing upgraded"

I'm guessing I need to go outside ubuntu-land in my "/etc/apt/sources.list", but I have no idea if I'm right - or where I'd go if I am.

The other thought I am having is at what point is my hardware limiting me on version upgrades?

Any assistance is very much appreciated.

---

### Post by asmoore82 on 2007-09-09
[https://wiki.ubuntu.com/CriticismFAQ#head-1663544b421081799ed551bdfa891411191121f2](https://wiki.ubuntu.com/CriticismFAQ#head-1663544b421081799ed551bdfa891411191121f2)

::You can drop the paranoia and just have FUN with Linux!

Welcome.

---

### Post by kamathews on 2007-09-09
... agreed - my choice of an AV might be silly (keep in mind I AM surfing the net without any at the moment - something I would never consider with my M$ machines....)

however, for educational purposes - the question remains (as I'm sure it will come up again with other more relevant packages...

---

### Post by asmoore82 on 2007-09-09
> **kamathews said:**
> ... agreed - my choice of an AV might be silly (keep in mind I AM surfing the net without any at the moment - something I would never consider with my M$ machines....)

however, for educational purposes - the question remains (as I'm sure it will come up again with other more relevant packages...

the long answer is that Ubuntu strives to be an extremely stable distro,
which, in my experience, means that it may not always have the newest versions of
packages available as they need time to be tested by Ubuntu staff.

Overall, I would say that Ubuntu is kept more "up-to-date" than Red Hat based distros such as
Fedora Core; but neither can ever be as "cutting-edge" as smaller "expert" distros such as archlinux.

However, I would never make a "How up to date is it" judgement based
on a highly unneccessary pakage such as Antivirus.

I particularly like to point out this line on the page I linked...
> [B]Out of the box, it[Ubuntu] is already more locked-down than a
Windows box with a commercial Firewall.[/B]

---

