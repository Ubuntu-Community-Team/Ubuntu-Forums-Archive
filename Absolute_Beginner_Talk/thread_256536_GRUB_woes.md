---
title: "GRUB woes"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-09-13
Hi, I installed ubuntu, and then installed windows xp afterwards. This wiped out my GRUB boot loader but obviously my ubuntu installation is still intact. How can I recover GRUB so to speak.

Hope someone can help with some basic instructions for a n00b.

Thanks..

---

### Post by Najand on 2006-09-13
Check out Ubuntu Wiki to get an fast, easy and complete reply:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Herman on 2006-09-13
Hello, tommy1987,
You just boot the Ubuntu Live CD and open up a terminal ('Applications --> Accessories --> Terminal'), and type some commands to overwrite the bootloader section of the Master Boot Record with code that will make it point to Grub in the Ubuntu partition again instead of to Windows.

The first command is 'sudo grub' to open a 'grub shell' ```
sudo grub
``` The next command is 'find /boot/grub/stage1'. That is to remind you which partition has Ubuntu on it in grub's numbering scheme. You'll need to use the number (answer) you get here as part of the next command```
find /boot/grub/stage1
``` The next command tells grub what partition to pay attention to, (your Ubuntu partition), and it will be one of the partitions you were just told in the previous command, normally (hda1) for a standard install, ```
root (hd0,1)
``` Where: (hda1) was the answer you received from the previous command. 

The next command is 'setup (hd0)', that installs the stage1 for grub in your Master Boot Record. ```
setup (hd0)
``` And the last command is 'quit' to quit the 'Grub Shell'.```
quit
```, then exit the terminal ```
exit
``` And finally, reboot to make sure it worked. 
Here's a link to a web-page to see the same thing again, but illustrated to make sure you can see what to do. [Click Here]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").

If you have any problems, please ask again, for more help.
Regards, Herman :D

---

