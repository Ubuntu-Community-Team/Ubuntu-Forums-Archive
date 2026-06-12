---
title: "vSuspend2disk failed on unloading 'rt2500'. Trying to recover."
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by defenestratos on 2008-02-14
Why when I try to hibernate does the computer tell me Suspend2disk failed on unloading 'rt2500'. Trying to recover.
I have Kpowersave installed as well and it does something similar. 
RT2500 must surely refer to my wireless card which is functioning normally in all other ways. If I have my external drive plugged in the computer can't shut that down either.
I'm a sixty four bit guy as well by the way.

---

### Post by talsemgeest on 2008-02-15
Must just be a problem with the drivers that a lot of people have been having

---

### Post by defenestratos on 2008-02-15
Does anybody have anything specific I can do to my system rather than just idle speculation? Tests or an explanation of the problem.

---

### Post by talsemgeest on 2008-02-15
Well if it is what I said it was, there is nothing you can do

---

### Post by defenestratos on 2008-02-16
What I mean is do you have a link to the bug report or thread where it is discussed? I travel a lot and need to power down frequently.

---

### Post by talsemgeest on 2008-02-16
Ok it does seem to be a problem with your wireless card, take a look here: [http://suseforums.net/index.php?showtopic=16575](http://suseforums.net/index.php?showtopic=16575)

---

### Post by defenestratos on 2008-04-07
Hey I just checked my  /var/log/suspend2disk.log and here is the readout. Seems it can't unload the RT2500 because it is 'in use'.



> hugo@hugo-laptop:~$ rmmod rt2500
ERROR: Module rt2500 is in use
hugo@hugo-laptop:~$ sudo rmmod rt2500
ERROR: Module rt2500 is in use
hugo@hugo-laptop:~$ sudo modprobe -r rt2500
FATAL: Module rt2500 is in use.
hugo@hugo-laptop:~$ rmmod rt2500
ERROR: Module rt2500 is in use
hugo@hugo-laptop:~$ joe /var/log/suspend2disk.log
Processing '/etc/joe/joerc'...done
Processing '/etc/joe/joerc'...done

























    I    /var/log/suspend2disk.log (  Row 166  Col 1    6:47  Ctrl-K H for help

== restore_after_sleep: restart and reload everything ==

Resuming:
---------

Reloading modules:
  uhci_hcd

Restarting services:
starting apcupsd:
##  /usr/lib/powersave/scripts//sleep_helper_functions: line 503: /etc/init.d/a
starting upsd:
##  /usr/lib/powersave/scripts//sleep_helper_functions: line 503: /etc/init.d/u
starting irda:
##  /usr/lib/powersave/scripts//sleep_helper_functions: line 503: /etc/init.d/i
starting slmodemd:
##  /usr/lib/powersave/scripts//sleep_helper_functions: line 503: /etc/init.d/s

Remounting filesystems:
  not necessary.


---

