---
title: "Raid questions"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by &lt;&lt;joe&gt;&gt; on 2008-01-22
I would like to set up a raid to boost my start up time and some other stuff
I have 2 hard drives that i would like to use but they are very different sizes 
80 gb and 250 gb 
right now i have Windows and Linux on the first disk and my home dir on the second disk
I just want to have Linux use the raid and i am not worried to much about drive falure because I back it up on to an external drive when I can.

So would it make sence to have the linux install in raid 0 (striped) aross both the disks?
and then have my home dir fill up the rest of the second disk

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-01-22
unless anyone sees a huge gaping problem i think i am going to do this
right now it takes me 43 seconds to boot to the log in screen and then another 5 after i press enter on my password
will tell you what its like after i set up the raid

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-01-22
bump

---

### Post by JRanch on 2008-01-22
Depending on your specific setup using RAID 0 (striping) can give a wide range of results, this depends mostly on the quality of the RAID controller and the pattern for use of the RAID array.  In the worst cases, poor controller and shallow access queue, a RAID 0 array can actually give decreased performance.

Some people have reported great improvements in startup times by using a static IP instead of DHCP, especially when using a wireless NIC.

You might also consider trying Xubuntu.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-01-23
Well I did it 
using the alternate install cd so software raid 
no real boot speed inprovement
but it didn't slow it down ether

---

