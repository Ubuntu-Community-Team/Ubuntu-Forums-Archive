---
title: "Some really strange time problem"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Tart on 2007-07-24
Greetings all,

Tomorrow will be a week since I installed Ubuntu, I'm loving it. But I have some really strange problem. Well, not really a problem rather annoyance. 

I have dual boot system. I installed Windows on hard drive #1, disconnected it and installed Ubuntu on hard drive #2. This way I have Windows and Ubuntu on two different hard drives, and if I mess up ubuntu (since I'm noob I expect to do this several times) Windows will not be affected and I can reinstall ubuntu without any issues.
 
I switch between systems by pressing F8 when computer starts, and it asks me what from what device I would like to boot (by default it is Windows).

Now here is my problem. 
1.I turn my computer and go into BIOS and set up clock to 12:00PM (I dont really have to do this step)
2.Boot into Windows, time is 12:00PM
3.Restart and boot into windows again time is still 12PM
4.Restart boot into Ubuntu time 12PM
5.Restart boot into Ununtu time 12PM
6.Restart and boot into Windows time 4PM


Both systems are on Eastern Time, and synchronization with Internet is disabled.

Any ideas? 

Thanks

---

### Post by bigfox on 2007-07-24
Windows always assumes that your computers system clock is set to local time.

Ubuntu asks you upon installation if you computer is set to UTC time.  (Universal Time Code)
With UTC, your computers system clock would be set the same regardless of where in the world you live.
The Operating system then off sets that by your time zone to get the local time.

Most computers system clocks are not set to UTC, so when the installer asks you if it is set to UTC, just tell it NO.

I am trying to figure out how to set it so Ubuntu knows that your system clock is set to local time.

Will post here once I figure it out.

---

### Post by bigfox on 2007-07-24
Here is a how to for disabling UTC
[http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_217.html](http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_217.html)

---

### Post by Tart on 2007-07-24
Thanks, I really appreciate it.

---

