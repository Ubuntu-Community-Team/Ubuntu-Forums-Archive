---
title: "Recovered most of my data..."
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by krazyman on 2007-07-16
Hi All,

I have recently had the HDD on my Ubuntu laptop start to fail. I have used a USB 2 IDE converter to connect it to my Ubuntu desktop, and got most of the files off no problem.

However, when I hit a corrupt bit of disc, my file manager windows freeze up, I cannot cancel the copy, and cannot umount the disc, as it says it is busy. I have to reboot to resume my recovery operations (and it doesn't even fully shut down, I have to hit the reset button).

What can I do to regain control of the disc, either by umounting and remounting, or ending a process? 

Many Thanks,

Andy

---

### Post by phr0ze on 2007-07-16
How about doing copy operations from the command line and if it locks up try ctrl-C. Another option is to kill your file manager. Open a terminal and type sudo killall NameofFileManager

---

### Post by krazyman on 2007-07-16
Yeah i think command line could be the way to go... when i was using nautilus killing it killed my desktop too... so i tried dolphin, which at least leaves the desktop intact, but still leaves the disc 'busy' so I can't continue without a reboot...
Will try command line next time, stand by!

---

### Post by krazyman on 2007-07-16
Ok tried the command line. CTRL-C doesn't work, has no effect at all. Tried CTRL-\ too but nothing.

So then I alt-F4'd the window, then as root tried kill -9 <pid>, which came back with nothing, but didn't kill the process...

well looks like it's curtains for the disk. I've got everything I want really...

---

### Post by bodhi.zazen on 2007-07-16
Try this :

[http://www.cyberciti.biz/tips/how-do-i-save-recover-data-from-crashed-disks-with-dd-and-ddrescue-command.html](http://www.cyberciti.biz/tips/how-do-i-save-recover-data-from-crashed-disks-with-dd-and-ddrescue-command.html)

---

