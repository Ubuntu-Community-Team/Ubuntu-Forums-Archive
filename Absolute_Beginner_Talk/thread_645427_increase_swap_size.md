---
title: "increase swap size"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by astromech on 2007-12-20
Hi Just installed 256 mb more of ram for a total of 512 mb swap is a bout 736mb or close to that .Should I increase the swap size and can doing this damage the current installation.?

PIII @733

---

### Post by jordanmthomas on 2007-12-20
Hi.
You can increase swap size by booting with your Ubuntu LiveCD and resizing the partitions with gparted.

Alternatively, you could create a swap file on disk:
To add a swap file:
1. Determine the size of the new swap file and multiple by 1024 to determine the block size. For example, the block size of a 64 MB swap file is 65536.
2. In a terminal, type the following command with count being equal to the desired block size:
```
sudo dd if=/dev/zero of=/swapfile bs=1024 count=65536
```
3. Setup the swap file with the command:
```
sudo mkswap /swapfile
```
4. To enable the swap file immediately but not automatically at boot time:
```
sudo swapon /swapfile
```
5. To enable it at boot time, edit /etc/fstab to include:
```
/swapfile   swap  swap defaults 0 0
```
The next time the system boots, it will enable the new swap file.

6. After adding the new swap file and enabling it, make sure it is enabled by viewing the output of the command cat /proc/swaps or by using the free command.

Hope this helps you out.


**EDIT**
you've edited your post now:
You should already have plenty of swap, so only add some if you run out of swapspace.

---

### Post by nikolas68 on 2007-12-20
I have a question: upon installation i've created a Swap of 4Gb that are just sitting there for nothing. How can i decrease it to 1Gb? (i have 2Gb Ram)
thanks

---

### Post by astromech on 2007-12-20
> **nikolas68 said:**
> I have a question: upon installation i've created a Swap of 4Gb that are just sitting there for nothing. How can i decrease it to 1Gb? (i have 2Gb Ram)
thanks

You can use the live cd as the previous poster has described just decrease in with the partitioner instead of increasing it.You could also use a live gparted cd.

---

### Post by bigken on 2007-12-20
with 2gig of ram you dont need a swap file

---

### Post by astromech on 2007-12-20
> **bigken said:**
> with 2gig of ram you dont need a swap file

Then he could just delete the swap partition entirely?

---

### Post by bigken on 2007-12-20
> **astromech said:**
> Then he could just delete the swap partition entirely?


yep

---

### Post by astromech on 2007-12-20
Below is my top readout I'm still wondering if the swap should be increased and would there be any performance gain?


top - 06:59:22 up  9:02,  2 users,  load average: 0.26, 0.39, 0.36
Tasks:  84 total,   3 running,  81 sleeping,   0 stopped,   0 zombie
Cpu(s): 22.1%us,  5.0%sy,  0.0%ni, 72.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    514896k total,   505716k used,     9180k free,    16440k buffers
Swap:   746980k total,    33808k used,   713172k free,   316596k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7540 root      15   0 88100  48m 9460 S 16.6  9.7  12:15.64 Xorg               
 8291  user     15   0 85188  14m 9208 R  9.3  2.9   0:01.21 xfce4-terminal     
 7600 user     15   0 75792 6344 4760 S  0.3  1.2   0:01.70 xfce4-session      
 7609 user    15   0 71232  10m 7180 S  0.3  2.1   0:05.97 xfwm4              
 7618 user    15   0 73056  12m 9300 S  0.3  2.6   0:07.49 xfce4-panel        
    1 root      18   0  2912 1848  524 S  0.0  0.4   0:02.20 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.21 events/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 khelper            
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
   30 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0          
   31 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   32 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  108 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  129 root      15   0     0    0    0 S  0.0  0.0   0:00.24 pdflush            
  130 root      15   0     0    0    0 S  0.0  0.0   0:00.24 pdflush            
  131 root      11  -5     0    0    0 S  0.0  0.0   0:00.55 kswapd0            
  132 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0              
 1905 root      10  -5     0    0    0 S  0.0  0.0   0:00.47 ata/0              
 1906 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux            
 1909 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0          
 1910 root      10  -5     0    0    0 S  0.0  0.0   0:00.70 scsi_eh_1          
 1912 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd      
 1913 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd              
 2172 root      10  -5     0    0    0 S  0.0  0.0   0:01.48 kjournald          
 2371 root      12  -4  2680 1028  376 S  0.0  0.2   0:00.80 udevd              
 3215 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused          
 3703 root      17   0  2844  864  648 S  0.0  0.2   0:00.04 pppd               
 3844 root      18   0  1652  508  440 S  0.0  0.1   0:00.00 getty              
 3845 root      18   0  1648  508  440 S  0.0  0.1   0:00.00 getty              
 3847 root      18   0  1652  508  440 S  0.0  0.1   0:00.00 getty              
 3851 root      18   0  1648  508  440 S  0.0  0.1   0:00.00 getty              
 3852 root      18   0  1648  508  440 S  0.0  0.1   0:00.00 getty              
 3857 root      18   0  1648  504  440 S  0.0  0.1   0:00.00 getty              
 4092 root      18   0  2256 1172  656 S  0.0  0.2   0:00.01 acpid              
 4198 root      23   0  1700  652  536 S  0.0  0.1   0:00.29 syslogd            
 4256 root      15   0  1788  520  432 S  0.0  0.1   0:00.47 dd                 
 4258 klog      18   0  2428 1376  400 S  0.0  0.3   0:00.26 klogd

---

### Post by bigken on 2007-12-20
they say give yourself twice your ram for swap 512mb=1gig swap how true this is 
Im not sure but it cant hurt

---

