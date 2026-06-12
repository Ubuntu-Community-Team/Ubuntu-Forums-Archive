---
title: "Dual boot OSX/Ubuntu on iMac fusion drive (step 3 install ubuntu ??)"
date: 2014-12-09
forum: Apple Hardware Users
---

### Post by UncleRoy on 2014-12-09
I have a 1.2 TB fusion drive iMac 8gb RAM. Wishing to put dual boot OSX(10.8.5)/Ubuntu under refind control.
Trial and erroring my way thru advice on <http://sourceforge.net/p/refind/discussion/general/thread/7bf6f4df/>
basically 3 steps 
1) partition the drive 
2) install refind
3) install ubuntu
I have completed 1 and 2

gParted Live now sees my partitions as  


/dev/sda1 fat32 EFI 200mb
/dev/sda2 hfs+ MacHD 531.34gb
/dev/sda3 hfs+ Recovery 619.89mb
unallocated 128.42mb
/dev/sda4 hfs+ REFIND 200.0mb
/dev/sda5 fat32 DATA 450(odd)gb
/dev/sda6 ext4 UBUNTU 20.0gb
/dev/sda7 linux-swap SWAP 8.0gb


I wish to install 14.04 on the partition sda6 (UBUNTU) using sda7 (SWAP) as the swap area (leaving the others untouched) 


Under advice from above webpage I must now 


"install Ubuntu with sda6 mounted as / and the boot loader installed on sda (ignore the warning about a boot partition)."
I just don't under stand the above line.


I go Ubuntu 14.04 bootstick -> "install ubuntu" - select "install alongside mac OSX"
and don't know what the above line means or what to to next.
Although i know what a terminal is I do not know every linux command
so please treat me as a dummy and offer very exact instructions.


Thanks in advance

---

### Post by slickymaster on 2014-12-09
*Moved to the ***Apple Hardware Users*** sub-forum*

---

