---
title: "What is using up my RAM?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by tango_ninja on 2008-02-25
I'm using gDesklets to monitor my RAM and CPU usage....and according to RAM monitor I'm using roughly 42% of my 1Gb of ram. this approximates to 426 Mb, and this number concurs with my System Monitor.

My question is...what using all that RAM? ???? I heard Ubuntu was light and only used a couple hundred Mb of ram for normal operations. 

See below, I have a shot of my System Monitor showing ram usage, and another shot of my processes taken 5s later.....if you add them up, they certainly don't add to 400+ Mb !!!

What is using my RAM ??

---

### Post by kaens on 2008-02-25
type "top" in a terminal to get an overview of what's using up memory.

---

### Post by Crafty Kisses on 2008-02-25
> **tango_ninja said:**
> I'm using gDesklets to monitor my RAM and CPU usage....and according to RAM monitor I'm using roughly 42% of my 1Gb of ram. this approximates to 426 Mb, and this number concurs with my System Monitor.

My question is...what using all that RAM? ???? I heard Ubuntu was light and only used a couple hundred Mb of ram for normal operations. 

See below, I have a shot of my System Monitor showing ram usage, and another shot of my processes taken 5s later.....if you add them up, they certainly don't add to 400+ Mb !!!

What is using my RAM ??

From the looks of it, Java is using 60MB.

---

### Post by tango_ninja on 2008-02-25
**@codename** yes i see that java is using about 60Mb....but 60Mb isn't 400....

---

### Post by macogw on 2008-02-25
```
free -m
```
The second line will list "cache."  That's the pre-fetched memory the OS has so that when you start a new process or more memory is requested, it can hand it off quickly.

```
top
```Press "M" once it's running to sort by memory usage.  Check the "resident" column.  The "virtual" column is just how much it thinks it has based on the cache.  All the processes are kind of tricked into thinking they own the cache since they can all grab from it if they need to.

---

### Post by Crafty Kisses on 2008-02-25
> **tango_ninja said:**
> **@codename** yes i see that java is using about 60Mb....but 60Mb isn't 400....

Yeah, post the following output:
```
top
```

---

### Post by tango_ninja on 2008-02-25
I'm not sure if i''m reading this correctly...but if I am it looks like a lot more memory is being used than i thought...

```
top - 21:45:00 up  1:51,  2 users,  load average: 0.99, 1.25, 1.04
Tasks: 133 total,   1 running, 131 sleeping,   0 stopped,   1 zombie
Cpu(s): 11.9%us,  1.7%sy,  0.0%ni, 84.1%id,  1.2%wa,  0.2%hi,  1.0%si,  0.0%st
Mem:   1026044k total,  1012396k used,    13648k free,    19260k buffers
Swap:  3004112k total,    34732k used,  2969380k free,   498316k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                         
 8046 andrew    15   0  137m  35m  19m S   10  3.6   3:27.77 rhythmbox                       
 8867 andrew    15   0  177m  76m  23m S    8  7.6   1:58.59 firefox-bin                     
 5360 root      15   0  432m  85m  16m S    3  8.5   9:25.61 Xorg                            
 6150 andrew    17   0 1232m  80m  20m S    2  8.1   3:40.64 java                            
 5795 andrew    15   0 53360  24m  12m S    2  2.4   2:05.34 python                          
 8362 andrew    15   0 95956  35m  17m S    1  3.6   1:50.69 deluge                          
 3828 root      13  -2  1744  384  280 S    0  0.0   0:26.15 ipw3945d-2.6.22                 
    1 root      18   0  2952 1852  532 S    0  0.2   0:01.48 init                            
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                     
    4 root      34  19     0    0    0 S    0  0.0   0:00.02 ksoftirqd/0                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                     
    7 root      34  19     0    0    0 S    0  0.0   0:00.01 ksoftirqd/1                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                      
    9 root      10  -5     0    0    0 S    0  0.0   0:00.06 events/0                        
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1                        
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper                         
   31 root      10  -5     0    0    0 S    0  0.0   0:00.01 kblockd/0                       
   32 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                       
   33 root      10  -5     0    0    0 S    0  0.0   0:00.39 kacpid                          
   34 root      10  -5     0    0    0 S    0  0.0   0:02.70 kacpi_notify                    
  160 root      10  -5     0    0    0 S    0  0.0   0:00.00 kseriod                         
  188 root      18   0     0    0    0 S    0  0.0   0:00.00 pdflush                         
  189 root      15   0     0    0    0 S    0  0.0   0:00.02 pdflush                         
  190 root      10  -5     0    0    0 S    0  0.0   0:02.59 kswapd0                         
  241 root      13  -5     0    0    0 S    0  0.0   0:00.00 aio/0                           
  242 root      13  -5     0    0    0 S    0  0.0   0:00.00 aio/1                           
 2152 root      10  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                   
 2153 root      14  -5     0    0    0 S    0  0.0   0:00.00 khubd                           
 2163 root      10  -5     0    0    0 S    0  0.0   0:01.13 ata/0   
```

---

### Post by igknighted on 2008-02-25
Run the command "free".  Linux uses free ram to buffer and preload, and will report the ram as used.  It is not, it will be available to any application that needs it.

Using the command free, it shows you what is actually used and what is buffered, see mine:
```
fitzgid@lappy:~> free
             total       used       free     shared    buffers     cached
Mem:        904712     879656      25056          0      69396     506704
-/+ buffers/cache:     303556     601156
Swap:      2634620          0    2634620
```

the middle row in the free column is actually what is free

see this link for details: [http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by tango_ninja on 2008-02-26
```
             total       used       free     shared    buffers     cached
Mem:       1026044    1000796      25248          0      23432     442028
-/+ buffers/cache:     535336     490708
Swap:      3004112      34704    2969408

```

so I have 490 Mb free?  I still wonder where the ram is going..

---

### Post by az on 2008-02-26
> **tango_ninja said:**
> ```
             total       used       free     shared    buffers     cached
Mem:       1026044    1000796      25248          0      23432     442028
-/+ buffers/cache:     535336     490708
Swap:      3004112      34704    2969408

```

so I have 490 Mb free?  I still wonder where the ram is going..

No, you have 2.5 MB free.

Unused ram is wasted ram.  How slow do you think your system would run if it reserved 90 percent of the ram for applications which were not running?

The trick is to be able to judge which things to dump from ram when something more important requires the memory.  Linux does that very well.

---

### Post by mali2297 on 2008-02-26
> **tango_ninja said:**
> ```
             total       used       free     shared    buffers     cached
Mem:       1026044    1000796      25248          0      23432     442028
-/+ buffers/cache:     535336     490708
Swap:      3004112      34704    2969408

```

so I have 490 Mb free?  I still wonder where the ram is going..

It is rather clear from the output of top:
rythmbox, firefox, X, java, python, deluge,...

---

### Post by movieman on 2008-02-26
Firefox can use a lot of memory; I think it's for the RAM cache where it stores recently visited pages for fast access. The X server tends to suck up more and more memory over time due to fragmentation, in the past I've found it's best to log out at least every couple of months so it can restart.

But, as mentioned, the operating system will try to use RAM to cache data when it's not being used by applications; and it seems much smarter than Windows, which swaps out applications to make space for big disk files that you'll never touch again. So long as the system isn't swapping you don't really need to worry.

---

### Post by K.Mandla on 2008-02-26
> **igknighted said:**
> see this link for details: [http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)
+1 for that link, it's a fantastic explanation of what's going on in your computer's little brain(s).

---

### Post by roaldz on 2008-02-26
The Gentoo docs have always been a good linux resource!

---

