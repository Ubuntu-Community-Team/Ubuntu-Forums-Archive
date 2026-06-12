---
title: "OFFLINE kernel  upgrade from 2.6.20 to 2.6.22"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by rave23 on 2007-09-18
hai  i would like to upgrade from kernel 2.6.20 to 2.6.22 . 
The main reason is that i bought a network card ( INTEX ) the driver given for that works only for kernels 2.4 and 2.5
further i found that its not a genuine chip set of realtek 8129 ( its actually sc92031 )
so it wouldnt work ... it worked for some usin ndiswrapper-1.47.tar.gz.

from recent news i found that this new kernel WILL support my card..

so plz help me update my kernel .......also i have downloaded linux-2.6.22.6.tar.gz
let me know how to upgrade WIHOUT internet connection ......

---

### Post by dcstar on 2007-09-19
> **rave23 said:**
> hai  i would like to upgrade from kernel 2.6.20 to 2.6.22 . 
The main reason is that i bought a network card ( INTEX ) the driver given for that works only for kernels 2.4 and 2.5
further i found that its not a genuine chip set of realtek 8129 ( its actually sc92031 )
so it wouldnt work ... it worked for some usin ndiswrapper-1.47.tar.gz.

from recent news i found that this new kernel WILL support my card..

so plz help me update my kernel .......also i have downloaded linux-2.6.22.6.tar.gz
let me know how to upgrade WIHOUT internet connection ......

This may be of use:

[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

### Post by rave23 on 2007-09-19
well since im new to linux .... my knowledge is restricted ....
but [http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974) refers to ONLINE update right ??

i mean sudo apt-get *** 

I NEED A PROPER STEP BY STEP SOLUTION FOR OFFLINE INSTALL ..
gve me the links  on every file i need to download ..

like linux linux-generic linux-dependencies ........ etc.........
thanks for the reply..

---

### Post by rave23 on 2007-09-20
I finally upgraded to kernel 2.6.22 ..........
and it DOES contain the driver sc92031 AND it is also loaded on startup ...... 

i confirmed this by checking..... 
 lsmod 

also i tried 
ping 192.168.1.1 and 127.0.0.1 ...
both retrieve packets at NO LOSS .. 

so obviously my intex card is working... 

BUT still i get message as ....... NO NETWORK DEVICES DETECTED  :(
i can see wired connection in network tools TAB and its set to automatic

PLZ HELP ... I KNOW IM REALLY CLOSE TO SOLVING IT ....

---

