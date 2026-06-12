---
title: "building first system, no signal to monitor..."
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by juanzo007 on 2008-01-12
Hey folks...

New linux user, decided to put together my own system, first timer.  wiz from Fry's guided me for harware selection.  Here tis:

asus p5gc-mx 1333 mother board for intel 945gc chipset
intel core duo processor E2180 2 Ghz
seagate sata 300 500gb hd.
lg dvd writer
big damn antec 500w tower

Anyway, the motherboard powers up, fans works, hd spins, dvd lites come on, but no signal to the monitor... Everything was easy on the setup, with the exception that my power led is three prong and the f panel wants two, couldn't connect. hdd led does not fire up when powered up.

Went thru the asus troubleshooting guide, d/c everything, clear cmos, check that the processor and ram are properly seated. no monitor signal...

Any suggestions?? Many thanks!!

---

### Post by overdrank on 2008-01-12
> **juanzo007 said:**
> Hey folks...

New linux user, decided to put together my own system, first timer.  wiz from Fry's guided me for harware selection.  Here tis:

asus p5gc-mx 1333 mother board for intel 945gc chipset
intel core duo processor E2180 2 Ghz
seagate sata 300 500gb hd.
lg dvd writer
big damn antec 500w tower

Anyway, the motherboard powers up, fans works, hd spins, dvd lites come on, but no signal to the monitor... Everything was easy on the setup, with the exception that my power led is three prong and the f panel wants two, couldn't connect. hdd led does not fire up when powered up.

Went thru the asus troubleshooting guide, d/c everything, clear cmos, check that the processor and ram are properly seated. no monitor signal...

Any suggestions?? Many thanks!!

HI and you hear no beeps, then try and remove the memory ( if you have more that one module then one at a time until none) and see if you get system beep. If not then you may want to remove the motherboard from the case and bench test it as it might be shorting inside the case.

---

### Post by juanzo007 on 2008-01-12
thanks so much!  user error, didn't connect the 4 prong 12v connector.

Now, when trying to install, it asks me to prepare partitions, but when i click "forward", i get the error message "not root system is defined"

if i go back, I just get keyboard layout selection...   funny tho, web access works, applications work...  Newb...

Thanks!!

---

### Post by juanzo007 on 2008-01-12
disregard, folks...  I'll post s new thread as it's a different problem...

---

### Post by overdrank on 2008-01-12
> **juanzo007 said:**
> thanks so much!  user error, didn't connect the 4 prong 12v connector.

Now, when trying to install, it asks me to prepare partitions, but when i click "forward", i get the error message "not root system is defined"

if i go back, I just get keyboard layout selection...   funny tho, web access works, applications work...  Newb...

Thanks!!

HI and if you are manually partitioning your drive you will need to set the mount point as root here is a example
[http://img216.imageshack.us/my.php?image=feistydual12tj0.png](http://img216.imageshack.us/my.php?image=feistydual12tj0.png)
And this link may help some
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

