---
title: "wireless problems"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by compuchem on 2007-03-05
Hi everyone, I just took the plunge and switched over to linux on my computer and am having trouble getting my wireless card running.  

I have a netgear wg111u which has two drivers, one of which is firmware.  After I installed them using ndiswrapper, I used ndiswrapper -l and it says "driver present, hardware present" for the firmware, but it only says "driver present" for the wg111u driver.  Is this the reason my card wont work? The LED isn't lit or anything.

Thanks for any advice

---

### Post by crispy_420 on 2007-03-05
No experience with that card/chipset but here are some links:

[http://doc.gwos.org/index.php/NetgearWireless](http://doc.gwos.org/index.php/NetgearWireless)

[http://doc.gwos.org/index.php/Bcm43xxDriver](http://doc.gwos.org/index.php/Bcm43xxDriver)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

[http://ubuntuforums.org/showthread.php?t=114922](http://ubuntuforums.org/showthread.php?t=114922)

Hope they help, good luck!

---

### Post by maniacmusician on 2007-03-05
> **compuchem said:**
> Hi everyone, I just took the plunge and switched over to linux on my computer and am having trouble getting my wireless card running.  

I have a netgear wg111u which has two drivers, one of which is firmware.  After I installed them using ndiswrapper, I used ndiswrapper -l and it says "driver present, hardware present" for the firmware, but it only says "driver present" for the wg111u driver.  Is this the reason my card wont work? The LED isn't lit or anything.

Thanks for any advice
yeah that could be it. Visit the List at the ndiswrapper wiki and make sure you're using a driver that works.

Also, when using ndiswrapper don't forget these crucial steps. After you install ndiswrapper, you have to do:

> sudo depmod -a
sudo modprobe ndiswrapper

---

### Post by compuchem on 2007-03-06
Thanks for the advice Crispy and Maniac.  I finally got ndiswrapper to list the hardware and the driver for both files.  It turns out that ndiswrapper makes a separate directory for both the firmware (athfmwdl in my case) and the driver (wg111u).  All I had to do was make sure that both directories had copies of all the same files and it clicked...

Now on to new problems.. my LED still isn't lit, and the networking gui doesn't list my wireless card.  When I run dmesg it gives me a bunch of ndiswrapper errors (because I don't have internet on that computer, I just hand typed them below):

ndiswrapper version 1.8 loaded (preemp=yes, smp=yes)
ndiswrapper (check_at_hdr:149) windows driver is not 64-bit; bad magic :010B 
ndiswrapper (load_sys_files:218): couldn't prepare driver 'athfmwdl'
ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for               messages from 'loadndiswrapper'
ndiswrapper: probe of 2-8:1.0 failed with error -22

I'm using an AMD-64 processor, and my guess from line 2 is that this may be part of the problem... bad magic indeed.  Any ideas?  Thank you soooo much for any help

---

### Post by maniacmusician on 2007-03-06
did you install the 64-bit version of Ubuntu? If so, then that just may be your problem. I've never dealt with it myself, but I'm under the impression that 64-bit Ubuntu (like every other OS) is a bear to work with, and not worth it.

I don't have any experience with 64-bit, but may I suggest reinstalling 32-bit?

---

### Post by compuchem on 2007-03-07
Ahh, that's probably it.. I do have the 64-bit version.  I'd rather not have to wrestle with my OS every time I want to do something, but do you know if I'll lose a lot of performance if I switch down to 32?

---

### Post by crispy_420 on 2007-03-07
I don't know about a loss in performance but expect to gain more support for software and hardware.

---

### Post by compuchem on 2007-03-07
Cool.. I'll try reinstalling with the 32-bit version when I get home.  I'll post again with whatever happens. Thanks!

---

### Post by compuchem on 2007-03-07
Success! I'm actually writing this post from my linux computer!  It turns out the problem was that I was running the 64-bit version of Ubuntu, hopefully that will all be ironed out in the future.  Disregard what I said earlier about making sure the files were the same in both the wg111u and athfmwdl directories.. ndiswrapper should take care of that on it's own.  Thanks for all the help Ubuntonians!

---

### Post by crispy_420 on 2007-03-07
Good luck switching to 32-bit. It is more software to install and most drivers are 32-bit anyway. Even in Windows, 64-bit is weak and lacking in hardware support.

---

