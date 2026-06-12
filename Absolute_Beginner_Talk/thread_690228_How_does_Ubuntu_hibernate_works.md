---
title: "How does Ubuntu hibernate works?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-02-07
Hi
Can some one explain how does Ubuntu hibernate feature supposed to works?
I tried to hibernate the computer (ubuntu 7.10) and it just come to a login page again.
I thought it should be like windows hibernate?

thanks

---

### Post by Michl on 2008-02-07
You will get a log-in window after you turn
on your computer after hibernating, but after
log-on, you will return to the screen you had
when you hibernated.

---

### Post by emarkd on 2008-02-07
Hibernate is supposed to write your current system state to the disk and shut down.  Suspend keeps everything in RAM and consumes just a bit of power, but nothing's running.  They're supposed to be very similar to what Windows does.  However, like lots of things in Linux, there are some non-free binary device drivers that don't play nice with the Hibernate/Suspend features.  If yours isn't working correctly, you've probably got one of those bits.  There are workarounds for some; try searching for that.

---

### Post by Telescope_Nerd on 2008-02-07
What graphics card are you using? I am using Nvidia 7 series I had this problem and managed to fix it by updating the nvidia drivers and making some changes to the config files. If you are using Nvidia too let me know and i'll post the config changes...

---

### Post by legolas_w on 2008-02-08
Thank you all for your reply.
Yes I am using NVidia 7100Gs and It would be very kind of you to share the instruction with me.
I do not know how to update the driver, but as far as I can say, my system is up to date with ubuntu update mechanism.

thanks

---

### Post by legolas_w on 2008-02-09
any one?

---

### Post by Telescope_Nerd on 2008-02-11
Hi legolas_w
sorry for the delayed reply I stopped watching this thread. So....
First step you need to enable the restricted drivers for you graphics card, this will also make Ubuntu look much nicer. So go to:

System -> Administration -> Restricted Driver Manager

and enable restricted drivers. You may have to restart after this. More details in this link:
[https://help.ubuntu.com/community/BinaryDriverHowto#head-3bce99fcdcae50501735bd4e639c85acc115c4c8](https://help.ubuntu.com/community/BinaryDriverHowto#head-3bce99fcdcae50501735bd4e639c85acc115c4c8)

Now if that doesn't fix your suspend/hibernate issues try these changes to the config file:
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

That worked for me, and I hope it works for you! but if not then there are likely some other config settings that need changing on your system. Best thing to do in this case is get searching the forums and wikis.

**[EDIT]** More discussion and an alternative fix can also be found here:
[http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html](http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html)

---

