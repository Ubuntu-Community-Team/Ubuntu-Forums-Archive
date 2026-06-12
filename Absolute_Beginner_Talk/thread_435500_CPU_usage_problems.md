---
title: "CPU usage problems"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2007-05-07
Hey all,

I just tried the switch from 6.10 to 7.04 on my laptop. After install it seemed to work fine, and it worked fine when I used the LiveCD. But after installing it, it started running one at 80%, which rapidly climbed to 90%, and then the other started climbing past 50% and I had to shut her down. Ironically I wasn't running anything at the time: no updates, I wasn't even trying to crack the wireless thing on here. Has anyone else had this happen?



Thanks :)
~Q

---

### Post by seetho on 2007-05-07
You can check to see what processes are chewing up your CPU cycles.  Go to System->Administration->System Monitor.

---

### Post by nonpareilpearl on 2007-05-07
Already did that, and it didn't show anything that would explain it. The only process that seemed to be using anything but 0% CPU was the System monitor itself-and even that was only 4%. (I had opened the System Monitor when my fans started flipping out to see what was going on, that's why I knew the percentages :) )

---

### Post by seetho on 2007-05-07
That's a little strange...

Try booting with a different kernel to see if you still get this problem.  Press ESC when GRUB boot which leads you to the GRUB menu.  By default you have the latest kernel and an older kernel on your install.  Choose the older kernel to try.

Otherwise I have no idea what could be wrong.  Sorry I can't help much.

---

