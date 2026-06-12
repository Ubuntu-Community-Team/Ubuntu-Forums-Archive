---
title: "Trying to install ubuntu, multiple problems, repartition manager error"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Sink41 on 2007-10-18
I am new to linux/ubuntu apart from using a knoppix live cd a couple of years ago. Anyway, i am trying to install it permenantly on 500gb hard drive with windows xp already installed. Although i want a permenant install i still want to use windows as my primary os, so i want a small partition for linux with most space left for windows.

My pc specs:
q6600 processor
2gb RAM
500gb hardrive with 292gb of free space, NTFS formatted
nvidia 640mb 6800gts
audigy 2 zs soundcard
Samsung 226bw monitor
gigabyte P35C-DSR motherboard

I am using the 64bit ubuntu 7.10 disk. When i boot off the cd the first thing i decide to do is verify the files. A window comes up saying "loading kernel" goes to 100% and then the screen goes black except two lines at the bottom which say something about loading the kernal. The screen then goes black and stays black. The cd-rom drive is active for another minute or two and then the computer goes quiet and just sits there with a black screen. I reboot and this time try test memory which loads up memtest+ fine, i reboot and this time try the top option boot/install linux. Same thing happens again. I reboot and this time manually set the VGA to lowest resolution. Black screen again. I do a google search and a thread where someone is advised to edit the boot options and remove "quiet" and "splash" so that an error message is seen. I do this and press enter, a load of text starts scrolling and eventually i get to the ubuntu desktop. The cd-drive is still spinning so it's not like i was impatient the other time.

Next thing i try to do is install ubuntu. It's going ok until i get to this screen

[[img]http://xs220.xs.to/xs220/07424/ubuntu.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs220&d=07424&f=ubuntu.png)

"use entire disk" sounds like its going to get rid of windows so i try the second option. An error (which i forgot to take a screenshot of) pops up and when i click ok i am greeted by this.

[[img]http://xs220.xs.to/xs220/07424/ubuntu2.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs220&d=07424&f=ubuntu2.png)

I am a bit concerned that the program which is going to repartition my precious windows disk seems a bit buggy. Or isn't working with my machine properly anyway. So i reboot into windows. What should i do?

---

### Post by Hobo Joe on 2007-10-18
Use Gparted to partition your hard drive, it's located under System > Administration > Gparted.

---

### Post by Sink41 on 2007-10-18
OK, i did that and created a 20gb partition, it crashed after creating the partition but this was when it was refreshing its view of the hard drive and the job had already been done. In fact i booted into windows at this point and though it did do a scan disk everything was ok.

I then tried to install ubuntu but the installer crashed while it was copying files saying either the cd-rom or hard drive was faulty (!) Windows now wont boot and i have tried mbrfix and bootfix in the windows recovery console to no avail. I am typing this in ubuntu and all my files are still there its just that the windows boot is screwed up dont know if you can help me with this. Here is what partition manager looks like:

[[img]http://xs220.xs.to/xs220/07425/partitions.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs220&d=07425&f=partitions.png)

I am guessing ticking boot on the main partition would work? but i really dont want to screw up my PC anymore please help me!

---

### Post by Sef on 2007-10-18
I would make the Windows partition your boot instead of a separate partition.

---

