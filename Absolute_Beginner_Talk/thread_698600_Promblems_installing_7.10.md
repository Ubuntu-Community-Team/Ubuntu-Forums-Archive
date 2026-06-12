---
title: "Promblems installing 7.10"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by Holmes89 on 2008-02-16
I'm having a bunch of difficulties installing 7.10 on a Western Digital internal hard drive. I installed 7.04 before with no difficulties but then wanted to try putting another operating system on so I wiped the drive. Now I am trying to go back and install 7.10 and I'm having a bunch of problems. Firstly it will not load a gui for the live cd. So I installed 7.04 again and installed it but when I upgraded to 7.10 it froze at startup. What do I have to do to get this working? I'm reformatting the drive again but is there something else wrong? (I currently have three hd in the computer. One for windows, one for ubuntu-desktop and one for ubuntu server)

---

### Post by taurus on 2008-02-16
Doesn't load the GUI from LiveCD has nothing to do with your harddrive.  It is because the LiveCD is having a little technical difficulty with your graphic card/monitor.  So, try using the safe mode from the boot menu or use the alternate CD to install Gutsy on your machine instead.

---

### Post by LacosteGirl23 on 2008-02-16
I don't actually have it installed on my laptop. I have a disk. And I just place that in and use it that way. I run Windows Vista. :)

---

### Post by Holmes89 on 2008-02-16
okay when I try to boot off of the live cd I get the same error for both safe mode and not safe mode:

udevd-event[2665]: run_program '/sbin/modprobe' abnormal exit
 

how do I fix this? Is this a corrupt disc?

---

### Post by taurus on 2008-02-16
There are a few steps you need to do.

1.  After downloading it to your machine, you need to run checksum to make sure the integrity of the ISO image is correct.

2.  Burn it as an ISO image file at a slow speed like 4x if you can.

3.  At the first boot screen from the CD, run the check disc for defects option to make sure the disc is good.

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29)

---

