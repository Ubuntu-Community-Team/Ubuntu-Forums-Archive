---
title: "G4 powerbook, dual-booting but fan noise terrible!"
date: 2009-12-17
forum: Apple Hardware Users
---

### Post by frankwakeman on 2009-12-17
After having never touched a Mac two days ago I've now repaired my friend's install of OS X 10.3 and added Ubuntu 9.10, the power pc version, burnt to DVD.

The second time I booted up the fan stayed on and was a dreadful racket.  Can this easily be sorted out?  (For the moment I have no wireless working either, but I imagine that after using an ethernet cable the restricted driver mentioned on the screen for Broadcom will put this right.)

If not I will just have to reinstall the Mac OS bootloader and unshrink the Mac partition (or reinstall from scratch if that can't be done).  It will be a shame as Ubuntu could get that machine out of its antiquated online experience in OS X 10.3, where no current browsers work (Opera 9 is the best fit) and no free antivirus seems to be available.

Thanks in advance for any info.

---

### Post by linuxopjemac on 2009-12-18
I found something on the fedora forums for you, which you can try...
> 
Found a hack to fix the problem
the problem centers around the temperature threshold at which the Linux kernel is instructing the G4 laptop to turn on the CPU fan to cool the CPU down
You can increase the threshold by 5C ... 5 degrees celsius in real time

echo 5 > /sys/devices/temperatures/limit_adjust

note the fan will kick in when you compile code or other CPU intensive activities

you can add the above string to /etc/rc.local
so that after the system fires up the temp threshold is increased 

original article [here]("http://www.fedoraforum.org/forum/showthread.php?t=61014")

Please let us know if it works.

---

### Post by frankwakeman on 2009-12-18
I very much appreciate your efforts.  However, I've totally run out of steam as far as putting this right goes.  I would have carried on for a while, but the wireless wasn't working even after activating the recommended driver, and I belatedly found out how bad the Ubu-Mac's Flashplayer substitutes are.  A shame really, as the person who owns the Mac was pleased at the point I thought I'd managed the dual-boot well, and this 1.3 ghz machine otherwise performs extremely well and looks lovely on a 17-inch screen.

When my friend goes on holiday next year I'll borrow the Mac again and see how 10.04 fares.  I've spent most of the days ince Wednesday doing this and I'm absolutely fried. But at least the Mac isn't.  :-)

---

### Post by serpetiello on 2011-07-15
+1: also works on Ubuntu 10.10, on a Powerbook G4 17".

Works with negative values as well: try using -15 (to simulate 15 degrees more than the sensor thinks there are) and watch the sensor1_fan_speed going up to almost 8000 rpm...

---

