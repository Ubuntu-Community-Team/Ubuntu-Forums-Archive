---
title: "troubleshooting high cpu (100%)?"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by HarmonicaGoldfish on 2007-10-06
Any ideas why? 

I am running gutsy. My cpu ran high most of the time with feisty but was much better under gutsy, however the cpu usage went wonky today, after the updates.

Is there anything I can do to reduce this?

thanks
[B]
***EDIT***This is a bug - I removed evms, rebooted and my cpu is down to around 10 instead of 100%,

See this bug report:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/130818](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/130818)[/B]

---

### Post by ryanVickers on 2007-10-06
Look in the System > Administration > System Monitor and see what's using all the processing power
or if your more familiar with the command line, type "top" (for table of processes)

---

### Post by HarmonicaGoldfish on 2007-10-06
that is what is odd. Nothing seems to be using processing power according to the system monitor. besides the system monitor itself...

---

### Post by ryanVickers on 2007-10-06
Hmm.  I know, Add the system monitor applet to the panel, and see if it's all black (not used), light blue (used), or dark blue (IO Wait (waiting on disk of other components)).

---

### Post by HarmonicaGoldfish on 2007-10-06
though, when I type top in terminal I get this:

harmonicagoldfish@harmonicagoldfish:~$ top

top - 15:05:40 up 22 min,  2 users,  load average: 2.73, 2.77, 2.35
Tasks: 107 total,   5 running, 101 sleeping,   0 stopped,   1 zombie
Cpu(s): 88.7%us, 11.3%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    516060k total,   507704k used,     8356k free,    15104k buffers
Swap:  1510068k total,        0k used,  1510068k free,   230428k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
 2556 root      21  -4 20460  18m  412 R 71.9  3.6  11:46.29 udevd             
 5376 root      15   0  110m  71m 8600 R  9.3 14.3   1:46.67 Xorg              
12121 harmonic  16   0 45736  19m  14m R  8.7  3.9   0:58.46 gnome-system-mo   
24705 root      23  -2 12496 1736 1392 R  0.7  0.3   0:00.02 evms_activate     
 4926 root      15   0  1840  540  444 S  0.3  0.1   0:08.76 dd                
 4928 klog      18   0  2480 1372  408 S  0.3  0.3   0:04.05 klogd             
21614 harmonic  15   0  2364 1148  876 R  0.3  0.2   0:00.22 top               
    1 root      15   0  2952 1856  532 S  0.0  0.4   0:01.72 init              
    2 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd          
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0       
    4 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0        
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0          
    6 root      14  -5     0    0    0 S  0.0  0.0   0:00.02 khelper           
   25 root      10  -5     0    0    0 S  0.0  0.0   0:00.07 kblockd/0         
   26 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid            
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify      
  100 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod

---

### Post by ryanVickers on 2007-10-06
could you just post a screenshot - that's really hard to read :)

but by the looks of it, "udevd" is the culprit.  Anyone know what it is? :p

** Edit: it seems to be something to do with the auto-mounting of devices. Could you post your "/etc/fstab" and "/etc/mtab" files?...**

---

### Post by HarmonicaGoldfish on 2007-10-06
It isn't showing any colour...just the system monitor icon. (green with yellow squiggle)

---

### Post by HarmonicaGoldfish on 2007-10-06
Yeah, that was pretty hard to read. Here's a screenshot:

[ATTACH]45480[/ATTACH]

In this one it shows the cpu usage at roughly 80%, though it pops around from 80 - 100 quite quickly.

---

### Post by HarmonicaGoldfish on 2007-10-06
I found this bug in launchpad

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/130818](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/130818)

one of the recommendations was to remove evms, which I am doing...I'll let you know what happens once I reboot :)

---

### Post by ryanVickers on 2007-10-06
Ok, I would also just check for a device that's constantly trying to mount but failing...

P.S. sorry I didn't reply sooner - the email notification must be malfunctioning :p

---

### Post by ryanVickers on 2007-10-06
Ok, actually, I found my udevd and it's taking 0 CPU, it's sleeping, taking 0KB or ram, and a nice value of -4 (rather high priority)

In the mean time - to speed things up, you may be able to lower the priority (make it like 19) to temporarily solve it....

---

### Post by ryanVickers on 2007-10-07
> **HarmonicaGoldfish said:**
> I found this bug in launchpad

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/130818](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/130818)

one of the recommendations was to remove evms, which I am doing...I'll let you know what happens once I reboot :)

It's been 10 hours - have you rebooted yet? :)

Edit:  It's been ***4 days*** - have you rebooted yet? :p (I think my record uptime was 651 hours ;))

---

### Post by ryanVickers on 2007-10-10
Ok, I saw you edited the first post - glad to here everything is back to normal (I guess - 10% still seems excessive! ;))

---

