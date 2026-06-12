---
title: "Really SLOW"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by 01100001 on 2008-03-11
Today I installed Ubuntu (again) and there are some problems that are really making me crazy ... First firefox is really slow, tab opening are slow, tam switching, tab closing etc.. I have firefox 2.0.0.12

Next, ALT+TAB Switches are REALLY! SLOW...
X-Chat tab clicking TO SLOW!
When I play clips on youtube the flash i terribly SLOW

I have no compiz enabled and all services that are unnecessary like bluetooth are disabled.... You may think that my computer is old, so here is its configuration :

CPU: 2.8 Inter Code 2 DUO 4MB CACHE
MB : Intel
RAM: 2GB 800 MHz
VGA: nVidia Geforce 8800GT 512MB DDR3

WHATS WRONG!?

---

### Post by glennric on 2008-03-11
Try running "top" in a terminal and see what is using all of the resources.

---

### Post by neurostu on 2008-03-11
better yet try running "htop" its a sexy version of top ;-)  

Did you see any processes taking large % of ram or cpu cycles?

---

### Post by Omnios on 2008-03-11
Did you install the nvidia driver. Default is the nv driver and you need the nvidia driver available on in the repositiries for 3d supoort etc.

---

### Post by glennric on 2008-03-11
One downside to htop is that is skews the data.  It shows up closer to top of its own list than top because it uses more resources.  Of course in the grand scheme of things 1 or 2 percent versus .1 or .2 percent is still not that big of a deal.

---

### Post by 01100001 on 2008-03-11
Yes... I installed the nvidia driver and all... 

Here is the "top" from terminal... and I see only firefox using the CPU a lot

top - 23:15:22 up  1:23,  2 users,  load average: 0.28, 0.60, 0.52
Tasks: 113 total,   1 running, 112 sleeping,   0 stopped,   0 zombie
Cpu(s): 19.1%us,  1.2%sy,  0.0%ni, 79.5%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1034492k total,   903056k used,   131436k free,    25248k buffers
Swap:  2080408k total,        0k used,  2080408k free,   578188k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 5760 aleks     16   0  245m  89m  26m S   35  8.9   9:54.99 firefox-bin                                                                                     
 5322 root      15   0 62204  48m 9112 S    4  4.8   3:33.17 Xorg                                                                                            
 6190 aleks     15   0 65056  20m  10m S    1  2.0   0:01.49 gnome-terminal                                                                                  
 6290 aleks     15   0 54472  37m 6916 S    0  3.7   0:29.62 wish8.5                                                                                         
    1 root      15   0  2952 1856  532 S    0  0.2   0:01.46 init                                                                                            
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                     
    4 root      34  19     0    0    0 S    0  0.0   0:00.01 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1

---

### Post by glennric on 2008-03-11
I am not sure what your problem is, but firefox is using a lot of resources.  More than it should be unless you took that data right at the moment you were loading several pages in firefox at the same time.

---

### Post by neurostu on 2008-03-11
Firefox is eating 35% of your cpu... What kind of pages are you looking at?

---

### Post by 01100001 on 2008-03-11
regular pages... HTML only ... and youtube sometimes... I don`t have this problem in windows ... I`m a bit disapointed from ubuntu

---

### Post by neurostu on 2008-03-11
hmmm.... I'm pretty sure its not ubuntu that is the problem. Do you have any plugins added on?  

You might want to try: 
```

sudo apt-get remove firefox
sudo apt-get install firefox

```

---

### Post by twright on 2008-03-11
you could try the latest firefox beta, it is a lot faster

also try fiddling with tracker's indexing settings, they can sometimes slow a system down.

this should help speed up firefox
```
sudo su
[SIZE=-1]cd /etc/modprobe.d/[/SIZE]
touch blacklist-ipv6
echo blacklist ipv6 >> blacklist-ipv6
```

---

### Post by 01100001 on 2008-03-11
I`ve tried uninstall/install .. I`ve tried firefox 3 Beta 3 .. still its really slow .. to slow :(

---

### Post by duruttye on 2008-03-11
Did you try with different web browsers?
Like Opera, Swiftweasel from automatix?

---

### Post by 01100001 on 2008-03-11
I`ve tried opera .. and its still slow :( :(

---

### Post by neurostu on 2008-03-11
Are things slow on the live CD?

---

### Post by 01100001 on 2008-03-12
Yes .. there to... Any idea anyone ?

---

### Post by daengbo on 2008-03-16
Your machine is quite fast, and I have one similar where everything screems. Your box should be quite responsive.
Please run "free" in a terminal and tell me the result. Also "tail /var/log/messages"

---

### Post by Wolfan on 2008-03-16
Could the problem be that you are running low on HD Space? Is there another OS installed (I.E. are you dual-booting?)

---

### Post by Wolfan on 2008-03-23
Hi there,

I don't know if you are still watching this post, but it hasn't been marked as Solved so I figure you might still be having this problem.  I ran into a problem similar to yours the other day after installing *xserver-xgl*.  I have a decent machine my self, but after installing this everything I had was running very slow, especially Firefox which when I checked *top* was taking up 39% just from sitting there.  It might not help, but check to see if it's installed and try uninstalling it.

---

### Post by frank002 on 2008-03-23
Disable IPv6 if you are running Gutsy. That should have Firefox running fast.

---

