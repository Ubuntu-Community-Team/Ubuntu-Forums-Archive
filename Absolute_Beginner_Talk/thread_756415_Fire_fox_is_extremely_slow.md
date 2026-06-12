---
title: "Fire fox is extremely slow"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by wil313 on 2008-04-15
Fire fox was running extremely slow so I installed another internet browser (Epiphany). Epiphany ran semi decent and now it is even slower then FireFox... I don't know why, everything else is just flying.... My computer has 1g memory and 1.3ghz so I know its not the computer... Any advice?

---

### Post by Crafty Kisses on 2008-04-15
While your running Firefox, post the following output:
```
top
```

---

### Post by namegame on 2008-04-15
what kind of internet connection do you have?

---

### Post by wil313 on 2008-04-15
> **Codename said:**
> While your running Firefox, post the following output:
```
top
```

Break it down a little bit more for me... ha Its been a long day...


I use a Broadcom card, but I know its not that, becuase I used it with other versions of Ubuntu and its worked fine... Firefox didn't start running so slow till some recent up dates were released.

---

### Post by Crafty Kisses on 2008-04-15
> **wil313 said:**
> Break it down a little bit more for me... ha Its been a long day...


I use a Broadcom card, but I know its not that, becuase I used it with other versions of Ubuntu and its worked fine... Firefox didn't start running so slow till some recent up dates were released.

While Firefox is running, open up the Terminal and type this in:
```
top
```
Then copy and paste what you see in the Terminal on the forums. :)

---

### Post by wil313 on 2008-04-15
```
 4877 root      15   0  373m  49m 7864 R  3.3  4.0   3:12.09 Xorg               
 6168 wil       15   0 66252  18m  10m S  1.3  1.5   0:00.46 gnome-terminal     
 5303 wil       15   0 18876  12m 5388 S  0.3  1.0   0:08.30 compiz.real        
    1 root      15   0  2948 1856  532 S  0.0  0.1   0:01.48 init               
    2 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:01.02 events/0           
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0          
   27 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   28 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  128 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod            
  147 root      17   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  148 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  149 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0   
```

---

### Post by HermanAB on 2008-04-15
You probably have a lame DNS in /etc/resolv.conf.

Test the DNS using 'dig' and put the fastest one at the top of the list.

Cheers,

Herman

---

