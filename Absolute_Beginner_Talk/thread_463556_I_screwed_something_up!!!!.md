---
title: "I screwed something up!!!!"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by rayj00 on 2007-06-03
Ok, I installed bootchart. Then I tried to figure out how to use it. 
Somewhere I seen where I had to change the info in grub/menu.lst
I added: kernel /vmlinuz-2.6.10 ro root=/dev/hda1 **init=/sbin/bootchartd**

Well, after I did a reboot, I can't get past BusyBox v1.1.3 
/bin/sh: can't access tty: job control turned off

BusyBox does not have an editor so I can't undo what I did.
This is serious!!! Help!!!

Ray

---

### Post by yabbadabbadont on 2007-06-03
When you get to the grub boot menu (hit esc if it doesn't show up by itself), hit the 'e' key to edit the entry.  Select the kernel line and hit 'e' again to edit that line.  Remove the "init=..." that you added and hit enter.  Press 'b' to boot using your change.  Once you are booted into Ubuntu, edit your menu.lst to remove what you added and then be sure to run "sudo update-grub".

---

### Post by rayj00 on 2007-06-03
Wow...Thanks for the quick response! Worked like a charm! 

My original problem is that its takeing nearly 1 1/2 minutes to boot Ubuntu 6.10.
Someone suggested installing bootchart. I did. Now how do I use it?

Thanks again......

Ray

---

### Post by rayj00 on 2007-06-03
OK, if only I did a little research first....

Looks like Nessusd is sucking up some CPU time during boot.....

Thanks!!!

Ray

---

