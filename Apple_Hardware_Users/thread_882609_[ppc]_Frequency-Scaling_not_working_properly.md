---
title: "[ppc] Frequency-Scaling not working properly"
date: 2008-08-07
forum: Apple Hardware Users
---

### Post by chimaera on 2008-08-07
Hi, 
when booting my 12" Powerbook G4, frequency-scaling is not working. Spaetz described the issue in [1], but his solution is not working properly. When editing the init-script like suggested and stopping/restarting powernowd, freq-scaling works, but if I reboot, it does not. I have to stop/start powernowd manually to get it work.    

Any ideas on this?

Thanks. 

[1] [http://ubuntuforums.org/showpost.php?p=4597008&postcount=38](http://ubuntuforums.org/showpost.php?p=4597008&postcount=38)

---

### Post by stream303 on 2008-08-09
I noticed this issue too with Powernowd on my iMac, and I could not get it to work either with a lot of cpufreq config files.

What *did* work, was to simply uninstall powernowd, and use CPUDYN instead.  Bingo!  Ok, cpudyn doesn't support on-demand either, but it will toggle very rapidly between power-save and performance.

This can actually be very desirable for those needing low-latency, such as with audio or other low latency requirements.  Makes for a snappier desktop too, since there is no "on-demand" state to deal with.

---

### Post by Oscar Pradilla on 2008-08-15
i found in this address the answer, now i can change between power profiles or make it run as i want..really easy

[http://hubpages.com/hub/Ubuntu--CPU-Scaling--Battery-life-and-You](http://hubpages.com/hub/Ubuntu--CPU-Scaling--Battery-life-and-You)

---

