---
title: "how to install headers?"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by nepenthean on 2005-11-22
I have been combing through the web on how to do this; however what I have uncovered has not worked. I am trying to install DC++ via cvs as described here  
[http://www.ubuntuforums.org/showthread.php?p=487927#poststop]("http://www.ubuntuforums.org/showthread.php?p=487927#poststop")
but am met with,

Did not find the bz2 library (bz2 compression)
Can't live without it, exiting
Note: You might have the lib but not the headers

after I typed, sudo scons.

I ran apt-cache search linux-headers, which returned,

linux-headers-2.6.12-9-386 - Linux kernel headers 2.6.12 on 386
linux-headers-2.6.12-9 - Header files related to Linux kernel version 2.6.12
linux-headers-2.6.12-9-686 - Linux kernel headers 2.6.12 on PPro/Celeron/PII/PIII/PIV
linux-headers-2.6.12-9-686-smp - Linux kernel headers 2.6.12 on PPro/Celeron/PII/PIII/PIV SMP
linux-headers-2.6.12-9-k7 - Linux kernel headers 2.6.12 on AMD K7
linux-headers-2.6.12-9-k7-smp - Linux kernel headers 2.6.12 on AMD K7 SMP
linux-headers-2.6.12-10 - Header files related to Linux kernel version 2.6.12
linux-headers-2.6.12-10-386 - Linux kernel headers 2.6.12 on 386
linux-headers-2.6.12-10-686 - Linux kernel headers 2.6.12 on PPro/Celeron/PII/PIII/PIV
linux-headers-2.6.12-10-686-smp - Linux kernel headers 2.6.12 on PPro/Celeron/PII/PIII/PIV SMP
linux-headers-2.6.12-10-k7 - Linux kernel headers 2.6.12 on AMD K7
linux-headers-2.6.12-10-k7-smp - Linux kernel headers 2.6.12 on AMD K7 SMP
linux-headers-386 - Linux kernel headers on 386
linux-headers-686 - Linux kernel headers on PPro/Celeron/PII/PIII/PIV
linux-headers-686-smp - Linux kernel headers on PPro/Celeron/PII/PIII/PIV SMP
linux-headers-k7 - Linux kernel headers on AMD K7
linux-headers-k7-smp - Linux kernel headers on AMD K7 SMP

I do not know where to go from here....

Any direction would be appreciated.  Thanks.

---

### Post by Brunellus on 2005-11-22
have you installed build-essential?

---

### Post by gord on 2005-11-22
```
 sudo apt-get install libbz2-dev 
```

---

### Post by nepenthean on 2005-11-23
Thanks very much, Gord! That worked. If you do not mind taking the time and since I am new here, what is that which you suggested to install? I mean, it is a library right? Is it right to say it is a developer tool?

---

