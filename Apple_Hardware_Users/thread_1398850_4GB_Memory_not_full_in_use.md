---
title: "4GB Memory not full in use"
date: 2010-02-05
forum: Apple Hardware Users
---

### Post by copyrights on 2010-02-05
Hallo,

I've just upgrade my macbook 5.1 (late 2008) to 4GB memory. I'm using ubuntu 8.10 x86_64, but don't get the full 4GB. 

```
>cat /proc/meminfo 
MemTotal:      3773544 kB
...

>uname -a
Linux manucodia 2.6.27-16-generic #1 SMP Tue Dec 1 19:26:23 UTC 2009 x86_64 GNU/Linux

```

Under mac os x there are 4096MB available.

What am I doing wrong?

---

### Post by saturnblackhole on 2010-02-05
your did nothing wrong it is common. theres a differ on standards between the hardware and software community on what a byte is. software does it in 12's where as hardware does it in 10's this leads to different reading on your computer. ubuntu recognizes your 4gb of hardware ram as 3773544 software ram.

its the same for my computer, i have 2gb of ram but ubuntu shows 1.9gb.

---

### Post by sxmaxchine on 2010-02-05
i think it is because ubuntu reserves a percentage of your ram for system files or something. not to sure if that is true though because i have never bothered to look into it

---

### Post by copyrights on 2010-02-05
mmh, but a byte are 8 bit :-)

so let's say it only was the difference between GB and GiB:

so /proc/meminfo displays 3773544 kB, if software show kiB that are 3773544 * 1024 = 3864109056 byte.

That is still 135890944 byte -> 135MB or 129MiB different to 4000000000 byte -> 4GB or 3.72GiB.

I think thats too much, I'd paid for that ;-)

---

### Post by buntuLo on 2010-02-05
correct me if i'm wrong: the Macbook 5,1 has only the nvidia 9400m graphics adapter, which uses part of your RAM memory (no idea how much). maybe OSX shows the total amount of RAM installed, and Linux only the one really available for the system?

---

