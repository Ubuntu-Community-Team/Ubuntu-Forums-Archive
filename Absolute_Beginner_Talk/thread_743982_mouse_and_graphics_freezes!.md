---
title: "mouse and graphics freezes!"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by linuxtoindia on 2008-04-03
mouse stops!
my mouse pointer in ubuntu 64bit 
skips again and again while even a lil process is running ...
is the any help to get rid of this


am having via chipset with 64mb grphics memory is this is the issue?
and 1.9ghz processor duo core

---

### Post by linuxtoindia on 2008-04-03
also i face some graphics problem in totem player

---

### Post by TeoBigusGeekus on 2008-04-03
Could you be a bit more specific about your graphics card?

---

### Post by linuxtoindia on 2008-04-03
i have on board graphics via chipset -motherboard ... it uses something k8m800   .. ram 512 dual boot with xp

---

### Post by TeoBigusGeekus on 2008-04-03
I hope this thread helps you....
[http://ubuntuforums.org/showthread.php?t=726994&highlight=k8m800]("http://ubuntuforums.org/showthread.php?t=726994&highlight=k8m800")

---

### Post by stefangr1 on 2008-04-03
Could you give your process table by running "top" in a terminal?

Also, could you give a processor benchmark by running:

time oowriter (2x please, second time should be faster)

Then I have yet another question. When did your computer get slow / when did you get mouse problems: did it happen at a specific moment in time after being normal before, or was it like this since the first time you installed Ubuntu?

---

### Post by linuxtoindia on 2008-04-03
15 total,   2 running, 113 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.8%us,  0.3%sy,  0.0%ni, 96.2%id,  0.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    446676k total,   426976k used,    19700k free,     1832k buffers
Swap:  1943824k total,    53940k used,  1889884k free,   120012k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
 5152 root      15   0  268m  20m 8940 S    4  4.7   1:04.04 Xorg                                                            
 5761 akshay    15   0  244m  22m  11m R    1  5.1   0:00.67 gnome-terminal                                                  
    1 root      17   0  5112 1924  532 S    0  0.4   0:01.70 init                                                            
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                     
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                     
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                      
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0                                                        
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1                                                        
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                         
   30 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                       
   31 root      10  -5     0    0    0 S    0  0.0   0:00.01 kblockd/1                                                       
   32 root      13  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                          
   33 root      13  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                    
  139 root      10  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                         
  175 root      15   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                         
  176 root      15   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                         
  177 root      10  -5     0    0    0 S    0  0.0   0:00.16 kswapd0                                                         
  230 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                           
  231 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                           
 2140 root      10  -5     0    0    0 S    0  0.0   0:00.00 ata/0                                                           
 2141 root      10  -5     0    0    0 S    0  0.0   0:00.00 ata/1                                                           
 2142 root      16  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                         
 2145 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                       
 2146 root      11  -5     0    0    0 S    0  0.0   0:00.01 scsi_eh_1                                                       
 2156 root      10  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                   
 2159 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                           
 2435 root      10  -5     0    0    0 S    0  0.0   0:00.13 kjournald                                                       
 2635 root      18  -4 20196  488  352 S    0  0.1   0:00.45 udevd

---

### Post by linuxtoindia on 2008-04-03
and processor benchmark

'' akshay@akshay-desktop:~$ time oowriter

real    0m16.175s
user    0m0.000s
sys     0m0.008s

---

### Post by linuxtoindia on 2008-04-03
any help would be highly appreciated!

---

### Post by stefangr1 on 2008-04-03
Your process table looks normal, you have close to 100% idle so nothing disturbing is running.

However, 16 seconds for oowriter seems somewhat slow. I have a c2d 2667Mhz that needs 4.5sec for that and a p3-1000Mhz that needs somewhere between 20 and 25 seconds. Off course, your computer should be closer to a c2d than to a p3.

It is possible that something is going wrong with scaling the processor frequency.

Could you run while stressing the CPU (very important!!):

cat /proc/cpuinfo

I think it might be an idea for you to try booting the computer using the noapic option.

To do that, you should enter grub at bootup, and subsequently press the "e" key.
Go to the line that starts with "kernel" and press "e" again. At the end of this line you add noapic, then you press enter to save. Now press esc another time to go back to the first menu, and press enter to boot.

If this doesn't work, I think you should consider installing the 32-bit Ubuntu edition.

---

### Post by linuxtoindia on 2008-04-04
here the output
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
stepping        : 1
cpu MHz         : 1899.998
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy misalignsse
bogomips        : 3804.49
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
stepping        : 1
cpu MHz         : 1899.998
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy misalignsse
bogomips        : 3800.15
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

---

### Post by linuxtoindia on 2008-04-04
> **stefangr1 said:**
> Your process table looks normal, you have close to 100% idle so nothing disturbing is running.

However, 16 seconds for oowriter seems somewhat slow. I have a c2d 2667Mhz that needs 4.5sec for that and a p3-1000Mhz that needs somewhere between 20 and 25 seconds. Off course, your computer should be closer to a c2d than to a p3.

It is possible that something is going wrong with scaling the processor frequency.

Could you run while stressing the CPU (very important!!):

cat /proc/cpuinfo

I think it might be an idea for you to try booting the computer using the noapic option.

To do that, you should enter grub at bootup, and subsequently press the "e" key.
Go to the line that starts with "kernel" and press "e" again. At the end of this line you add noapic, then you press enter to save. Now press esc another time to go back to the first menu, and press enter to boot.

If this doesn't work, I think you should consider installing the 32-bit Ubuntu edition.
even in 32bit it showed the same problem so i tried 64bit!!

shud i increase ram?

---

### Post by stefangr1 on 2008-04-04
First: nothing appears to be wrong with the processor scaling (some have experienced a problem where their processor stays at a low frequency to save energy even when it should not), yours it at 1900Mhz as it is suppozed to.

Also, from what your process table shows, I assumed that you are not running Compiz / desktop effects or that they are not causing a problem, if otherwise you could try disabling them. Did you already install the proprietary drivers as another poster advised?

More memory could help, but I'm not sure how much, since 450mb + enough swap (which you have) should not give problems.

I'm very sorry to say that I'm running out of ideas what else to try here.

---

### Post by linuxtoindia on 2008-04-04
i dont use any desktop effect!
and further
i have not installed any drivers
after installing ubuntu... is it neccesary??
moreover  it says ;;'you donot require any restricted drivers''

---

### Post by stefangr1 on 2008-04-04
If you install the drivers your video chip is used more efficiently. This can especially make a difference in performance when you are gaming, watching video, or using desktop effects. For normal desktop work with desktop effects disabled, however, your computer should work fine without proprietary drivers.

If you haven't installed the ATI drivers yet, you could definitively give it a try.

---

### Post by linuxtoindia on 2008-04-04
which kinda drivers?


i have via chipset 
on board graphics card

---

### Post by stefangr1 on 2008-04-04
OK, then I think you have a VIA video chip. You can download the drivers from this site:

[http://www.viaarena.com/default.aspx?PageID=2&Type=3](http://www.viaarena.com/default.aspx?PageID=2&Type=3)

---

### Post by linuxtoindia on 2008-04-04
how to install these drivers??
and yestery i installed xorg somelike ati drivers

---

### Post by linuxtoindia on 2008-04-04
how to install these drivers??
and yesterday
y i installed xorg somelike ati drivers

---

### Post by stefangr1 on 2008-04-05
Just have a look at an earlier post in this thread, of TeoBigusGeekus.

---

