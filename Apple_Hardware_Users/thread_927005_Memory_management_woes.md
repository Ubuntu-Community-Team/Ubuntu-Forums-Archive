---
title: "Memory management woes"
date: 2008-09-22
forum: Apple Hardware Users
---

### Post by aws910 on 2008-09-22
Whenever a memory-intensive process is run, it encounters many errors.  I have a macbook pro penryn(?) with 4GB memory.  The way this manifests itself is when I process a large file using ffmpeg: the output has a scratchy sound.  Another way I've noticed this is when I try to play a 5-track recording in ardour - sound output skips a lot.  This system is supposedly top-of-the-line, so I don't think it's a horsepower issue.  For some reason, I can't get it to use the swapfile.

I posted more detail in another forum on this site, but I guess I posted in the wrong place because I got no response:
[http://ubuntuforums.org/showthread.php?p=5786837#post5786837](http://ubuntuforums.org/showthread.php?p=5786837#post5786837)

---

### Post by Yannick Le Saint kyncani on 2008-09-22
Hi aws910,

- First, your system only use 3G ram when you have 4G. I suppose that's because you've installed 32bits ubuntu. 64bits ubuntu would use all 4G ram (assuming you have a 64bits cpu).

- Out of your 3G ram, 2G is used for cache, the remaining by your various programs. This is a very healthy situation. It means you won't gain anything by using 4G ram instead of 3G.

- As for the audio skipping from time to time, you may try the linux-rt kernel (sudo apt-get install linux-rt, and then reboot and choose the realtime kernel). And it may not change anything.

- You could also paste the output of "top", so that we can see if your system is on its knees cpu/io-wise.

Just my .02$

---

### Post by aws910 on 2008-09-22
Thanks a lot, I'll try that tonight and see if it helps.

---

### Post by cyberdork33 on 2008-09-22
macs tend to have issues with the realtime kernel, but goodluck.

---

### Post by aws910 on 2008-09-24
Wow, you were right.  Installed the RT kernel and output is still scratchy.

Here's the output of top at idle:
```
top - 10:52:27 up  1:53,  3 users,  load average: 0.33, 1.33, 1.91
Tasks: 167 total,   2 running, 165 sleeping,   0 stopped,   0 zombie
Cpu(s): 11.2%us,  2.6%sy,  0.0%ni, 84.8%id,  0.0%wa,  1.0%hi,  0.3%si,  0.0%st
Mem:   3063428k total,   794204k used,  2269224k free,    13756k buffers
Swap:  8193140k total,    40020k used,  8153120k free,   304564k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                                                         
 6524 mr        20   0 88464  29m  14m S    0  1.0   4:39.43 nautilus                                                                                                                                                                        
 6839 mr        20   0  269m 150m  24m S    4  5.0   4:36.08 firefox                                                                                                                                                                         
 6166 root      20   0  899m  67m  41m R   10  2.3   3:57.28 Xorg                                                                                                                                                                            
 5874 root      20   0 13344 1068  732 S    2  0.0   2:16.58 pommed                                                                                                                                                                          
 1487 root     -51  -5     0    0    0 S    1  0.0   1:31.24 IRQ-16                                                                                                                                                                          
 6593 mr        20   0  130m  89m  42m S    7  3.0   1:11.76 compiz.real                                                                                                                                                                     
 1454 root     -51  -5     0    0    0 S    0  0.0   0:53.27 IRQ-19                                                                                                                                                                          
    6 root     -51  -5     0    0    0 S    1  0.0   0:52.93 softirq-timer/0                                                                                                                                                                 
   19 root     -51  -5     0    0    0 S    0  0.0   0:29.01 softirq-timer/1                                                                                                                                                                 
   23 root     -51  -5     0    0    0 S    0  0.0   0:28.53 softirq-tasklet                                                                                                                                                                 
   10 root     -51  -5     0    0    0 S    0  0.0   0:22.28 softirq-tasklet                                                                                                                                                                 
  202 root      15  -5     0    0    0 S    0  0.0   0:19.32 kswapd0                                                                                                                                                                         
 9391 root      20   0     0    0    0 S    0  0.0   0:18.36 pdflush                                                                                                                                                                         
 6520 mr        20   0 15200 2660 1764 S    0  0.1   0:17.79 gnome-screensav                                                                                                                                                                 
   22 root     -51  -5     0    0    0 S    0  0.0   0:16.39 softirq-block/1                                                                                                                                                                 
 6522 mr        20   0 44640  23m  14m S    0  0.8   0:15.62 gnome-panel                                                                                                                                                                     
    9 root     -51  -5     0    0    0 S    0  0.0   0:15.40 softirq-block/0                                                                                                                                                                 
 6812 mr        20   0 70252  30m  18m S    0  1.0   0:15.30 pidgin                                                                                                                                                                          
 1618 root     -51  -5     0    0    0 S    0  0.0   0:12.96 IRQ-20                                                                                                                                                                          
 5668 root      20   0  1872  540  444 S    0  0.0   0:07.70 dd                                                                                                                                                                              
  200 root      20   0     0    0    0 S    0  0.0   0:07.59 pdflush                                                                                                                                                                         
 1567 root     -51  -5     0    0    0 S    0  0.0   0:07.02 IRQ-17                                                                                                                                                                          
 5670 klog      20   0  3804 2720  424 S    0  0.1   0:06.46 klogd                                                                                                                                                                           
 6754 mr        20   0 20936 8368 7068 S    0  0.3   0:05.58 multiload-apple                                                                                                                                                                 
 6613 mr        20   0 44140  15m 9.9m S    0  0.5   0:05.08 nm-applet                                                                                                                                                                       
 6743 mr        20   0 20780  11m 7012 S    0  0.4   0:04.88 gtk-window-deco                                                                                                                                                                 
 5524 root      15  -5     0    0    0 S    0  0.0   0:03.98 kondemand/0                                                                                                                                                                     
 6504 mr        20   0 26832 4084 3284 S    0  0.1   0:03.73 pulseaudio                                                                                                                                                                      
 5616 syslog    20   0  1936  680  532 S    0  0.0   0:03.27 syslogd                                                                                                                                                                         
   11 root     -51  -5     0    0    0 S    0  0.0   0:03.17 softirq-sched/0                                                                                                                                                                 
 6496 mr        20   0 40072  10m 8080 S    0  0.3   0:02.86 gnome-settings-                                                                                                                                                                 
10740 mr        20   0 37128  16m  10m S    0  0.6   0:02.47 sensors-applet                                                                                                                                                                  
 6597 mr        20   0 37132  16m   9m S    0  0.5   0:02.37 update-notifier                                                                                                                                                                 
 6941 mr        20   0 28684  13m 7824 S    0  0.5   0:01.88 notification-da                                                                                                                                                                 
   26 root     -51  -5     0    0    0 S    0  0.0   0:01.81 softirq-rcu/1                                                                                                                                                                   
   13 root     -51  -5     0    0    0 S    0  0.0   0:01.79 softirq-rcu/0                                                                                                                                                                   
 6432 mr        20   0  7304 4396 1904 S    0  0.1   0:01.64 gconfd-2                                                                                                                                                                        
 3181 root      16  -4  2420  968  384 S    0  0.0   0:01.54 udevd                                                                                                                                                                           
 6064 root      20   0  3420 1144  988 S    0  0.0   0:01.54 hald-addon-stor                                                                                                                                                                 
   24 root     -51  -5     0    0    0 S    0  0.0   0:01.48 softirq-sched/1                                                                                                                                                                 
 5944 haldaemo  20   0  6492 4548 3632 S    0  0.1   0:01.47 hald                                                                                                                                                                            
11243 mr        20   0 80804  21m  11m S    3  0.7   0:01.47 gnome-terminal                                                                                                                                                                  
 2163 root      15  -5     0    0    0 S    0  0.0   0:01.37 scsi_eh_0                                                                                                                                                                       
   72 root     -51  -5     0    0    0 S    0  0.0   0:01.23 IRQ-9                                                                                                                                                                           
    1 root      20   0  2844 1692  544 S    0  0.1   0:01.05 init                                                                                                                                                                            
 2954 root      15  -5     0    0    0 S    0  0.0   0:00.84 kjournald                                                                                                                                                                       
 6635 mr        20   0 22032 2668 2204 S    0  0.1   0:00.81 gvfsd-trash                                                                                                                                                                     
 2509 root      15  -5     0    0    0 S    0  0.0   0:00.70 usb-storage                                                                                                                                                                     
 6594 mr        20   0 23172 8572 6296 S    0  0.3   0:00.66 bluetooth-apple                                                                                                                                                                 
 6756 mr        20   0 30588  13m 8860 S    0  0.4   0:00.60 fast-user-switc                                                                                                                                                                 
 2157 root      15  -5     0    0    0 S    0  0.0   0:00.59 ata/1                                                                                                                                                                           
11237 mr        20   0 44668  18m  11m S    0  0.6   0:00.57 gedit                                                                                                                                                                           
 2156 root      15  -5     0    0    0 S    0  0.0   0:00.55 ata/0                                                                                                                                                                           
 6612 mr        20   0 24420  12m 7168 S    0  0.4   0:00.53 python                                                                                                                                                                          
    8 root     -51  -5     0    0    0 S    0  0.0   0:00.52 softirq-net-rx/                                                                                                                                                                 
   21 root     -51  -5     0    0    0 S    0  0.0   0:00.51 softirq-net-rx/                                                                                                                                                                 
 6021 root      20   0  3416 1156 1004 S    0  0.0   0:00.50 hald-addon-inpu                                                                                                                                                                 
 6530 mr        20   0 41544 3560 2448 S    0  0.1   0:00.42 bonobo-activati                                                                                                                                                                 
   30 root      -2  -5     0    0    0 S    0  0.0   0:00.41 events/1                                                                                                                                                                        
11275 mr        20   0  2440 1168  856 R    1  0.0   0:00.41 top                                                                                                                                                                             


```

And the output of top while processing said wmv->wav ffmpeg task:

```
top - 10:56:28 up  1:57,  3 users,  load average: 2.70, 1.85, 1.96
Tasks: 168 total,   1 running, 167 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.4%us,  3.6%sy,  0.0%ni, 14.2%id, 73.2%wa,  1.0%hi,  1.5%si,  0.0%st
Mem:   3063428k total,  1136592k used,  1926836k free,    11604k buffers
Swap:  8193140k total,    40020k used,  8153120k free,   636968k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                                                         
11375 mr        20   0 14756 2564 1368 D    6  0.1   0:08.26 ffmpeg                                                                                                                                                                          
 6166 root      20   0  899m  67m  41m S    4  2.3   4:11.01 Xorg                                                                                                                                                                            
 6839 mr        20   0  269m 150m  24m S    3  5.0   4:45.84 firefox                                                                                                                                                                         
 2954 root      15  -5     0    0    0 D    2  0.0   0:01.73 kjournald                                                                                                                                                                       
 5874 root      20   0 13344 1068  732 S    2  0.0   2:20.99 pommed                                                                                                                                                                          
    9 root     -51  -5     0    0    0 S    1  0.0   0:16.37 softirq-block/0                                                                                                                                                                 
 1487 root     -51  -5     0    0    0 S    1  0.0   1:34.05 IRQ-16                                                                                                                                                                          
 6593 mr        20   0  130m  89m  42m S    1  3.0   1:16.06 compiz.real                                                                                                                                                                     
    6 root     -51  -5     0    0    0 S    1  0.0   0:54.30 softirq-timer/0                                                                                                                                                                 
   19 root     -51  -5     0    0    0 S    1  0.0   0:29.86 softirq-timer/1                                                                                                                                                                 
   22 root     -51  -5     0    0    0 S    1  0.0   0:17.19 softirq-block/1                                                                                                                                                                 
11378 mr        20   0  2440 1160  852 R    1  0.0   0:00.03 top                                                                                                                                                                             
   10 root     -51  -5     0    0    0 S    0  0.0   0:23.05 softirq-tasklet                                                                                                                                                                 
   23 root     -51  -5     0    0    0 S    0  0.0   0:29.34 softirq-tasklet                                                                                                                                                                 
 1454 root     -51  -5     0    0    0 S    0  0.0   0:53.91 IRQ-19                                                                                                                                                                          
 1567 root     -51  -5     0    0    0 S    0  0.0   0:07.21 IRQ-17                                                                                                                                                                          
 1618 root     -51  -5     0    0    0 S    0  0.0   0:13.34 IRQ-20                                                                                                                                                                          
 5670 klog      20   0  3804 2720  424 S    0  0.1   0:06.64 klogd                                                                                                                                                                           
11359 root      20   0     0    0    0 D    0  0.0   0:00.13 pdflush                                                                                                                                                                         
    1 root      20   0  2844 1692  544 S    0  0.1   0:01.05 init                                                                                                                                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                                                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.29 migration/0                                                                                                                                                                     
    4 root      RT  -5     0    0    0 S    0  0.0   0:00.00 posix_cpu_timer                                                                                                                                                                 
    5 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-high/0                                                                                                                                                                  
    7 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-net-tx/                                                                                                                                                                 
    8 root     -51  -5     0    0    0 S    0  0.0   0:00.52 softirq-net-rx/                                                                                                                                                                 
   11 root     -51  -5     0    0    0 S    0  0.0   0:03.24 softirq-sched/0                                                                                                                                                                 
   12 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-hrtimer                                                                                                                                                                 
   13 root     -51  -5     0    0    0 S    0  0.0   0:01.83 softirq-rcu/0                                                                                                                                                                   
   14 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                                                                                      
   15 root      10 -10     0    0    0 S    0  0.0   0:00.00 desched/0                                                                                                                                                                       
   16 root      RT  -5     0    0    0 S    0  0.0   0:00.10 migration/1                                                                                                                                                                     
   17 root      RT  -5     0    0    0 S    0  0.0   0:00.00 posix_cpu_timer                                                                                                                                                                 
   18 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-high/1                                                                                                                                                                  
   20 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-net-tx/                                                                                                                                                                 
   21 root     -51  -5     0    0    0 S    0  0.0   0:00.51 softirq-net-rx/                                                                                                                                                                 
   24 root     -51  -5     0    0    0 S    0  0.0   0:01.49 softirq-sched/1                                                                                                                                                                 
   25 root     -51  -5     0    0    0 S    0  0.0   0:00.00 softirq-hrtimer                                                                                                                                                                 
   26 root     -51  -5     0    0    0 S    0  0.0   0:01.85 softirq-rcu/1                                                                                                                                                                   
   27 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                                                                                      
   28 root      10 -10     0    0    0 S    0  0.0   0:00.00 desched/1                                                                                                                                                                       
   29 root      -2 -20     0    0    0 S    0  0.0   0:00.30 events/0                                                                                                                                                                        
   30 root      -2  -5     0    0    0 S    0  0.0   0:00.42 events/1                                                                                                                                                                        
   31 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                                                                                         
   66 root      15  -5     0    0    0 S    0  0.0   0:00.15 kblockd/0                                                                                                                                                                       
   67 root      15  -5     0    0    0 S    0  0.0   0:00.17 kblockd/1                                                                                                                                                                       
   70 root      15  -5     0    0    0 S    0  0.0   0:00.12 kacpid                                                                                                                                                                          
   71 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                                                                                                    
   72 root     -51  -5     0    0    0 S    0  0.0   0:01.27 IRQ-9                                                                                                                                                                           
  157 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                                                                                                         
  199 root      -2  -5     0    0    0 S    0  0.0   0:00.00 krcupreemptd                                                                                                                                                                    
  202 root      15  -5     0    0    0 S    0  0.0   0:19.64 kswapd0                                                                                                                                                                         
  203 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                                                                                                           
  204 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                                                                                                           
  804 root     -51  -5     0    0    0 S    0  0.0   0:00.00 IRQ-8                                                                                                                                                                           
 1442 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                                                                                                   
 1443 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                                                                                                           
 2156 root      15  -5     0    0    0 S    0  0.0   0:00.57 ata/0                                                                                                                                                                           
 2157 root      15  -5     0    0    0 S    0  0.0   0:00.61 ata/1                                                                                                                                                                           
 2158 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux       
```

I see ffmpeg alternating between R and D status...

---

### Post by Yannick Le Saint kyncani on 2008-09-24
Yep, your system is spending all its time waiting for I/O (you have 73% WAiting for i/o).

Basically, you're screwed, because the so-called solutions are :

1- Copy all your data in a tmpfs and create the converted file in this tmpfs, but you can only do that if the size of wmv+wma is less than half your ram (which never happens).

2- Enhance the performance of I/O (buy faster drives, ...) but that means a lot of money.

3- Or, my preferred solution, run i/o and cpu intensive operations when you're not using your box (at night).


No 3 being the most practical solution, obviously.

---

### Post by aws910 on 2008-09-24
Ouch.  I was told this was a brand new, top of the line macbook pro... Core 2 duo T8300 w 4gb ram, and when I ran the test, most other programs were closed.  Should I stop running Compiz and Firefox?

---

### Post by Yannick Le Saint kyncani on 2008-09-25
> **aws910 said:**
> Should I stop running Compiz and Firefox?

You could try, nothing to loose, right :)

I don't think it will make any difference though. Your cpus are 15% idle and you have unused ram, so I think your problem is I/O-related.

If your wmv you want converted is less than 1G, you could try this though :

- Open a terminal.

- cd /the/directory/which/holds/the/wmv/file/

- cat mywmvfile.wmv >/dev/null

Then try the encoding again. This would fill your ram with the wmv file in cache. Then, assuming the wmv file is small enough and you still have ram free, the entire wmv file will stay cached and ffmpeg won't have to read it from the disk.

Your best bet would be to run cpu, ram and i/o intensive applications at night though.

---

### Post by aws910 on 2008-09-25
Thanks for the ideas!  

I closed firefox, disabled compiz, cached the file, then tried ffmpeg'ing it, no luck.  Tried recompiling ffmpeg with --enable-extra-warnings, thought that option and the rebuild with the rt headers might solve it, but no luck.  Maybe I'll try again tomorrow.

I like your idea of "doing it at night", don't know why it took so long to realize what you were saying :) ... I do have another machine I could script the recordings/transcoding on, run the job at night, then just copy it to a usb stick and go.

---

