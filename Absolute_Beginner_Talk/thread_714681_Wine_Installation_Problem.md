---
title: "Wine Installation Problem"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by mikkko on 2008-03-04
i followed the instructions stated here:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)


and i got this message:
The following packages have unmet dependencies:
  wine: Depends: libaudio2 but it is not installable
E: Broken packages

i need you help coz i need to use programs in windows for my school.. thanks

---

### Post by quibbler on 2008-03-04
your best bet is to use Synaptic Package Manager...

System - Administration - Synaptic Package Manager.

search for wine and install... this will also install any dependencies.

good luck

quibbler

---

### Post by mikkko on 2008-03-04
i already tried synaptics but it gives me this problem:

wine:
 Depends: libaudio2  but it is not installable

---

### Post by Joeb454 on 2008-03-04
What do you get if you run the following from a terminal:
```
sudo apt-get install libaudio2
``` you will be asked for your password (it won't show any typing though :))

---

### Post by mikkko on 2008-03-04
it gives me this...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libaudio2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libaudio2 has no installation candidate


i also tried downloading the latest version of wine and it was run by package installer, and it said "Error: Dependency is not Satisfiable: libaudio2"

i dont know what to do anymore... :confused:

---

### Post by Joeb454 on 2008-03-04
Have you enabled all software sources (except the CD) in System>Administration>Software Sources?

It is a known bug in WINE, but it's worth seeing if you can install libaudio2 manually :)

---

### Post by mikkko on 2008-03-04
i think enabling all the software sources did it..

thank you..

---

### Post by wthoang on 2008-04-25
> **Joeb454 said:**
> Have you enabled all software sources (except the CD) in System>Administration>Software Sources?

It is a known bug in WINE, but it's worth seeing if you can install libaudio2 manually :)

I hate to bring this topic bak...but i was having the same problem...and i was wondering if by enabling all software sources u mean like the universal,multiberse,rescricted and main? cos ive done this and i have still failed...

---

### Post by Joeb454 on 2008-04-25
Yes that is what I meant :) Though I assume you are running Ubuntu 8.04 and I have no experience with installing Wine on this release sorry :(

---

### Post by wthoang on 2008-04-26
no...not 8.04..7.10

---

### Post by JafaarNhh on 2008-04-26
you can install it at add remove applications search for Wine Windows emulator

---

