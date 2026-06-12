---
title: "X is acting up following reboot"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2007-01-22
So this is already the Nth time I have had problems with X not functioning.  I had recently downloaded envy ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) that automaticly updated my nvidia drivers, which worked beautifully.  Upon rebooting, however, I get a similar message that I did last time (which originally promped me to use envy).  I ran envy again, this time it doesnt work.  

I also have a fatal error this time that reads:  

"FATAL: Could not open '/lib/modules/2.6.17-10-generic/volatile/nvidia.ko': No such file or directory"

As a quick fix, I did the following:

sudo cp /lib/modules/2.6.17-10-generic/kernel/drivers/vido/nvidia.ko /lib /lib/modules/2.6.17-10-generic/volatile/nvidia.ko

and restarted x.  This seemed to work, albeit it took me into recovery mode I think (no desktop items, could not reboot from the gui).  Upon rebooting again, however, I encounter the same problem with the same error message, and my /.../nvidia.ko that I had previously copied is no longer there.  

Does anyone have any ideas?

Thanks

---

### Post by carlosfocker on 2007-02-08
Try this post

[http://www.ubuntuforums.org/showthread.php?t=344070]("http://www.ubuntuforums.org/showthread.php?t=344070")

and this one 

[http://ubuntuforums.org/showthread.php?t=291915]("http://ubuntuforums.org/showthread.php?t=291915")

---

