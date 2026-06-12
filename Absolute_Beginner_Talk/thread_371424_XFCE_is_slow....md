---
title: "XFCE is slow..."
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by mechel on 2007-02-26
My family computer is pretty old so I have decided to install xfce to use instead of gnome. My computer only has about 248 MB of ram and I have heard that that is plenty for xfce, but its still running very slow. It is constinly using 210 or more ram even when nothing is open and when i check the processes there is nothing that really justifys so much ram being used. Thunder bird takes more then 30 seconds to open and everything is just sluggish. 

Any help would be greatly appericiated! :)

---

### Post by sardion on 2007-02-26
Modern linux "uses" memory for nothing... it will always appear to be mostly used, this is due to readahead and other things.  So that statistic does not indicate what you think it does, it does not mean you are running out of memory.

How fast is your processor?

Thunderbird is slow, even on my 1.6GHz machine (also running XFCE) with 768MB RAM.  So is firefox.  I would strongly recommend swiftfox ([http://getswiftfox.com](http://getswiftfox.com)) ... I don't think there is an alternative to Thunderbird yet, all I can say is set to autostart (in the xfce settings) and treat it as part of the boot up process, that's what I do.

Wish there was better news.

---

### Post by sardion on 2007-02-26
You should disable any services you don't need.  There are lots of posts in hte forums about this.

Search for "boot up speed" and things of that ilk.  Removing things will speed up xfce a lot.

---

### Post by igknighted on 2007-02-26
> **mechel said:**
> My family computer is pretty old so I have decided to install xfce to use instead of gnome. My computer only has about 248 MB of ram and I have heard that that is plenty for xfce, but its still running very slow. It is constinly using 210 or more ram even when nothing is open and when i check the processes there is nothing that really justifys so much ram being used. Thunder bird takes more then 30 seconds to open and everything is just sluggish. 

Any help would be greatly appericiated! :)

Could you post the results of the command 'top' please?  Also, linux will always report to be using the max of ram.  It uses the excess ram not used by applications for general caching (after all, unused ram is wasted ram), but that ram is immediately freed up should an application need it.

If I had to guess, I would guess your problem is related to a missing graphics driver.  What type of graphics processor do you have?

---

### Post by mechel on 2007-02-26
home@home-desktop:~$ top

top - 19:56:31 up 1 day,  2:19,  2 users,  load average: 1.11, 0.89, 0.79
Tasks:  98 total,   1 running,  96 sleeping,   0 stopped,   1 zombie
Cpu(s):  0.7% us,  0.0% sy,  0.0% ni, 99.3% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    254916k total,   251984k used,     2932k free,      400k buffers
Swap:   738948k total,   103548k used,   635400k free,    23844k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5400 root      15   0  155m 9.9m 3068 S  0.3  4.0  11:00.73 Xorg
17442 home      16   0  2196 1104  856 R  0.3  0.4   0:00.19 top
    1 root      16   0  1568  236  208 S  0.0  0.1   0:01.44 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.91 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.20 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:03.42 kblockd/0
    9 root      10  -5     0    0    0 S  0.0  0.0   0:13.12 kacpid
  121 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  120 root      15   0     0    0    0 S  0.0  0.0   0:04.22 kswapd0
  708 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
 1829 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1946 root      15   0     0    0    0 S  0.0  0.0   0:02.31 kjournald
 2210 root      12  -4  2432  176  172 S  0.0  0.1   0:00.49 udevd
 3011 root      20   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event

My gpu is an onboard intel extreme AGP 32MB (by the way where is the place to look at your hardware in xfce?). Is Autostart like msconfig in windows, and where are the hte forums?
Thank you for your help so far!

---

### Post by mechel on 2007-02-26
Hmm i cant seem to find the thing that i used in gnome to view my different hardware is there something like that in xfce or do i need to download a new one?

P.S. How do you disable services?

P.P.S. Im going to bed, but ill try to be up early tomorrow to answer anything thats come up.

---

