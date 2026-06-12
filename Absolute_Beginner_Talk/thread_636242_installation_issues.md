---
title: "installation issues"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Jerome420 on 2007-12-09
I am brand new to using Ubuntu and Linux for that matter.  This morning I installed Ubuntu 7.10 on my Pentium 4 laptop (a 2004 model) that runs XP SP2.  Now when I try to boot Ubuntu I just get a fuzzy gray screen.  I have no problems getting XP to load, nor do I have any issues getting the Ubuntu Live CD to run.  I ran a CD diagnostic test on my disk (it is a copy from a friend) and it checked out fine.  I also searched for ways to fix the Grub boot file but cannot even find an actual example of what the boot string is supposed to say.  Any help you can provide would help.  Thanks.

---

### Post by kle on 2007-12-09
This sometimes happens on laptops with special screen drivers. 
On my laptop (which is an HP Pavillion) I had to add a couple of words to the command line calling the ubuntu kernel. 

You will probably find a lot of literature if you google your laptop and ubuntu. 

You might try my coctail - it will only apply for the one run and will not harm your system. Assuming you have a dual boot and thus also a Grub menu: 
1) click "e" when you reach the grub.
2) go to  the line starting "kernel"
3) click "e" again
4) go to end of line and add: noapic irqpoll

If this works you will have to permanently add the two words to the grub menu in terminal. 
Good luck

---

### Post by Jerome420 on 2007-12-09
thanks for the reply.  added lines to end of kernel line and same results.  any other suggestions??

---

### Post by kle on 2007-12-10
None other than reinstalling. I must have reinstalled a dozen times before I finally got everything right. (But now everything IS truly very right, and much better than on Windows).  
I would recommend installing from a so-called "alternate CD". 

If you are dual booting I recommend the link 
[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

On this page Herman slowly and in detail takes you through partitioning with the partitions windows, root, home, access to windows (Fat32) and swap, which I think is generally the most recommended setup. 

One thing however: when you reach the partition part, delete each of your current partitions (all but the first - windows) before returning to his recipe. 

Good luck

---

