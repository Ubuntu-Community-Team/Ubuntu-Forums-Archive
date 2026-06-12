---
title: "high cpu usage in gutsy"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-10-28
[PHP]30790 root      25   0  1752  544  452 R  100  0.0 594:32.83 mysqld_safe        
 7371 root      25   0  1756  548  452 R  100  0.0  12:40.11 mysqld_safe        
 6478 root      15   0  111m  54m 8868 S    0  1.6   2:31.70 Xorg               
    1 root      18   0  2948 1856  532 S    0  0.1   0:01.15 init               
    2 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/0        
    4 root      34  19     0    0    0 S    0  0.0 140:20.05 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      34  19     0    0    0 S    0  0.0  92:13.50 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:01.24 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   31 root      10  -5     0    0    0 S    0  0.0   0:00.08 kblockd/0  [/PHP] 

the results of top are above. Any idea why the mysql is taking up so much cpu?

---

### Post by P4man on 2007-11-11
FWIW you're not alone:
[http://ubuntuforums.org/showthread.php?p=2368931](http://ubuntuforums.org/showthread.php?p=2368931)

Did you try killing the Mysql processes and rebooting?

---

