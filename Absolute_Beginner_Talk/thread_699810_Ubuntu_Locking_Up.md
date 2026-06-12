---
title: "Ubuntu Locking Up"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2008-02-17
So, my comp seems to be locking up, I've never had these issues, the only thing I noticed is that every time it locks, Firefox is running in the background. Is there anyway I can fix this or figure out if it's truly Firefox or what?? I'd appreciate any help on this! Thanks everyone!

---

### Post by spiderbatdad on 2008-02-17
maybe something in the system log. have you tried disabling ipv6?

---

### Post by Tumpster on 2008-02-17
No I have not, how do I check the system log and what and how do I take care of IPV6?

---

### Post by spiderbatdad on 2008-02-17
system log is found under System>>Administration>>System Log

To remove disable ipv6...for security or performance: [http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

Many also disable it in the firefox browser by entering "About:config" (no quotes) and scrolling down to this section:

```
network.dns.disableIPv6
``` and right click on the word "false" select toggle and it will set to "true."

---

### Post by Crafty Kisses on 2008-02-17
> **Tumpster said:**
> So, my comp seems to be locking up, I've never had these issues, the only thing I noticed is that every time it locks, Firefox is running in the background. Is there anyway I can fix this or figure out if it's truly Firefox or what?? I'd appreciate any help on this! Thanks everyone!

Hmmm, post the following output, let's see what's actually running:
```
top
```

---

### Post by Tumpster on 2008-02-17
Here you are:
craig@craig-desktop:~$ top

top - 18:34:58 up 20 min,  2 users,  load average: 0.34, 0.34, 0.29
Tasks: 121 total,   1 running, 120 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.3%us,  0.3%sy,  0.0%ni, 97.0%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2075944k total,   736376k used,  1339568k free,    48876k buffers
Swap:  3229024k total,        0k used,  3229024k free,   409500k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5579 root      15   0  856m  61m 9620 S    3  3.0   1:46.28 Xorg               
 7133 craig     15   0  163m  58m  29m S    1  2.9   0:12.47 amarokapp          
 6010 craig     15   0 47604  27m   9m S    0  1.3   0:06.09 compiz.real        
    1 root      15   0  2948 1852  532 S    0  0.1   0:01.40 init               
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.06 events/1           
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   31 root      14  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0



I also went in and switched IPV6 to true, it was marked false so I fixed that.

---

### Post by Tumpster on 2008-02-17
Two things that changed right around the time this began, 
1) I had to completley remove/reinstall firefox due to it not saving passwords
2)I als recently loaded up Amaraock song player due to a growing distaste for XMMS although I think it was doing this before hand. I'm trying rythmbox right now to see if it still happens.


So far since running Rhythmbox for 30 minutes now with firefox running and no lock ups but I also fixed the IPV6 so I'm gonna run Amarock and see if it locks up with that running.

EDIT: No problems with amarock either, running last 25 minutes with no lockups. Maybe it was just the IPV6. Any ideas?

---

### Post by Tumpster on 2008-02-18
It's still doing this even after an unistall and reinstall, all times, firefox is open, it does it at random with no real thing that triggers is. When firefox is closed the comp runs flawlessly, any way I can detect this before it happens??

---

### Post by pemur1 on 2008-02-25
I didn't see the point in starting a new thread for the same problem, except that I'm not running Firefox in the background. I installed Amarok today, but my problem started yesterday. So Amarok's not the cause. Any assistance would be greatly appreciated.

---

