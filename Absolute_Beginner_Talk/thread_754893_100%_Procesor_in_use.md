---
title: "100% Procesor in use"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Vamp381 on 2008-04-14
After installing ubuntu 7.10 my processor is always in use.Help ;-/

Here is output 
```
top - 15:31:55 up 8 min,  2 users,  load average: 1.62, 1.58, 0.85
Tasks: 112 total,   2 running, 110 sleeping,   0 stopped,   0 zombie
Cpu(s): 16.1%us,  7.0%sy, 34.2%ni,  7.6%id, 34.1%wa,  0.3%hi,  0.7%si,  0.0%st
Mem:    515356k total,   506248k used,     9108k free,    82764k buffers
Swap:   746980k total,        4k used,   746976k free,   186112k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5480 pavle     34  19 30168  10m 2408 S  9.9  2.0   0:35.26 trackerd           
 9528 pavle     39  19  7048 2600 1888 R  3.9  0.5   0:00.02 w3m                
 4780 root      15   0 43168  29m 9072 S  2.0  5.9   0:13.76 Xorg               
 5890 pavle     15   0  143m  54m  20m S  2.0 10.8   0:33.44 firefox-bin        
    1 root      18   0  2948 1856  532 S  0.0  0.4   0:01.25 init               
    2 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   25 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0          
   26 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  111 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  133 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  134 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  135 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 kswapd0 
```

---

### Post by hyper_ch on 2008-04-14
tracker is using a lot or resources. I deactivated it as I don't need it... no clue what w3m is...

---

### Post by Vamp381 on 2008-04-14
I deactivated,same problem thou ^_^

---

### Post by hyper_ch on 2008-04-14
well, it will take a "little" while and just keep top running... although I prefer htop...

---

### Post by Vamp381 on 2008-04-14
Now its 0 (-;.Tnx

---

### Post by hyper_ch on 2008-04-14
tracker will index document files on your computer and uses quite some cpu... I don't need that and deactivated it...

---

### Post by girijesh on 2008-04-14
100% processor use, hard disk spinning always at peak and freezing of mouse and keyboard even after 15 minutes of inactivity at old PC hardware having P3 processors are the DEMERITS of ubuntu and I failed to find a solution for the same. Though enthusiasts have posted solutions but  they are not functional for hardwares I use.

It was the reason why I had to shift to PCLinuxOS as main OS for the PCs installed in school.

---

### Post by Vamp381 on 2008-04-14
Do u i need always to deactivate when turning on computer ?

---

### Post by hyper_ch on 2008-04-14
you can either 

(a) stop the daemon from starting at bootup (and starting it manually when needed)
(b) deinstall it completely
(c) let it run and hope that on sub-sequentiel updates it won't stress the cpu as much anymore

---

### Post by Vamp381 on 2008-04-14
How to stop Daemon (btw i upraged feisty not clean install)

---

### Post by xeth_delta on 2008-04-14
> **Vamp381 said:**
> How to stop Daemon (btw i upraged feisty not clean install)

To stop a service/daemon:
```
sudo /etc/init.d/service_name stop
```

To prevent a daemon from loading at start-time:
You can try to install sysv-rc-conf and deactivate the service from runtime level 5.

To start it just type in a terminal
```
sudo sysv-rc-conf
```
exit pressing q.

Please **be very careful** with what you disable and do it only and only if you know what you are doing or you could in some cases get into trouble.

---

### Post by Seisen on 2008-04-14
> **hyper_ch said:**
> tracker is using a lot or resources. I deactivated it as I don't need it... no clue what w3m is...

w3m is a text-based browser like, links or lynx.

---

### Post by xeth_delta on 2008-04-14
> **hyper_ch said:**
> tracker is using a lot or resources. I deactivated it as I don't need it... no clue what w3m is...

You can find out what a program is with the command "whatis" or by having a look at the manual:
```
whatis w3m
man w3m
```

---

### Post by Vamp381 on 2008-04-14
Thank you all.I will try that commands

---

