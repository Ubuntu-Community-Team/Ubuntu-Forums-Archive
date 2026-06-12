---
title: "&lt;cntr&gt; &lt;alt&gt; F1"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by 1two34 on 2008-04-13
After replacing my obsolete CRT monitor with a wide flatscreen monitor, (using Gutsy Gibbon) when I do <cntr> <alt> F1 to go to a command console the output to my monitor turns off and I have no command console, but then I <cntr> <alt> F7 and my desktop returns. Any suggestions?

---

### Post by llamakc on 2008-04-13
The TTY's are handled differently these days in Ubuntu. Try CTRL-ALT-F2

---

### Post by 1two34 on 2008-04-13
same thing happens with  CTRL-ALT-F2

---

### Post by llamakc on 2008-04-13
That is weird. Did you just swap the monitors or did you also reboot yet?

---

### Post by wormser on 2008-04-13
I found a [thread]("http://ubuntuforums.org/showthread.php?t=754065&highlight=tty") on this issue.  Following the trail it led to this [post]("http://ubuntuforums.org/showpost.php?p=4683002&postcount=15").

> i had this problem, but instead of going thru all the steps here, all i did was delete the 'vga=xxx' parameter in my /boot/grub/menu.lst. That's right, DELETE. Now my ttys work

---

### Post by 1two34 on 2008-04-13
many reboots since new monitor, (changed monitor last november) can't remember last time i tried TTY in Gutsy although I thought i had done it with this new monitor but since then I have installed many updates and programs
I think I will wait for the Ubuntu devs to fix this. Thank you wormser for the thread.

---

