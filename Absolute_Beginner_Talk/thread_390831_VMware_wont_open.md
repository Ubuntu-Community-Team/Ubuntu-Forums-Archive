---
title: "VMware wont open"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-03-22
i had vmware working perfect. I rebooted my PC and it wont launch.
In a terminal I get this:

```
ben@ben-ubuntu:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

ben@ben-ubuntu:~$ sudo /usr/bin/vmware-config.pl
Password:
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.

ben@ben-ubuntu:~$ 
```

---

### Post by jkeyes0 on 2007-03-22
I've had that problem before. Go into your system monitor (you can right click a panel on the desktop and click 'Add to panel', and add in a system monitor if you don't have one), and kill any process starting with "vm". Hopefully, that will take care of it. Then you should be able to run the vmware-config.pl file.

---

### Post by charles.g.moore on 2007-03-22
you could also just pull up a terminal

top

find the pid's associated with VM

sudo kill <pid #>

---

### Post by ProjectWhat on 2007-03-22
It says nothing about VM:
```
ben@ben-ubuntu:~$ top

top - 13:26:15 up  2:04,  4 users,  load average: 0.21, 0.22, 0.27
Tasks: 114 total,   1 running, 111 sleeping,   0 stopped,   2 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    515364k total,   496440k used,    18924k free,    11976k buffers
Swap:  1510068k total,      232k used,  1509836k free,   241864k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
    1 root      16   0  1632  532  448 S  0.0  0.1   0:01.16 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 events/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    7 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0          
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
   77 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  110 root      15   0     0    0    0 S  0.0  0.0   0:00.05 pdflush            
  111 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush            
  112 root      15   0     0    0    0 S  0.0  0.0   0:00.11 kswapd0            
  113 root      19  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0              
 1702 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd              
 1727 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt 
```

---

### Post by jkeyes0 on 2007-03-22
top only shows the top X processes (does not show everything that's running). Instead, try
```
ps aux
```
That will show all processes running, and you can find the ones that have VM in the name that way.

---

### Post by dragonfyre13 on 2007-03-22
> **charles.g.moore said:**
> you could also just pull up a terminal

top

find the pid's associated with VM

sudo kill <pid #>

God no.

Top is good for monitoring the **TOP** usage processes, but for finding any more, it's not the tool.

Execute this on the command line, and look for the processes starting with vm.

```
ps -ef | grep vm
```

Next to those, it should list the PID. Then you just

```
sudo kill -9 PID#
```

and you are golden.

---

### Post by ProjectWhat on 2007-03-22
> **jkeyes0 said:**
> top only shows the top X processes (does not show everything that's running). Instead, try
```
ps aux
```
That will show all processes running, and you can find the ones that have VM in the name that way.

Thank you that worked perfectly!!!!

---

