---
title: "Hard-disk and Update Problems."
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by rhc on 2008-01-05
Hi,i'm new to linux and so ubuntu.
I downloaded **"wubi"** today and i build **ubuntu** on my computer.
I have also Windows XP on my computer.
I'm  a completely newbie.I have basic **xp** knowledge.
I'm sayin' this because if you advise something to me about the problems i'll write,maybe i can't understand,so if you write those like telling to a dumb,i ll be very happy.

After i installed ubuntu from windows installer (wubi),i first saw the desktop then some clikcs.
I fell in love with the design.
I really loved it.

Now i have two questions,problems.

After i first opened ubuntu, the system advised me to download and install new updates from internet.

There were 176 updates and it took so long.
While it s installing them i want to delete something from my hardisk.
I have 1 hard disk and divided into 2 parts before.
Volume c: and volume d:
When i want to delete som files from D: it gave me an error.
But volume c: don't give same message,no problem about c: .

This is a read-only disk. You can't make change.
When i want to change it to "read and write" it said,you have no permissons.
This was my first prob.,i don't know what to do.

Secondly,after the updates finished,i restart the system,but in the boot menu where i chose ubuntu or windows,it gave me error  that "invalid boot.ini file,starting from windows".

Then i reinstalled ubuntu from wubi,so i think i  turned before the updates status,and it didn't give the same boot.ini message,ubuntu started normally just like i installed first.
I think i have problems about update.

If you help me,i ll be so happy cause i loved ubuntu.

(i use the word "problem" 1000 times,sorry for bad english)

---

### Post by Daveth on 2008-01-05
well, welcome to the Ubuntu forum first of all.
I'm assuming you installed ubuntu on partition d, with a standard grub bootloader giving you the option to go into XP or ubuntu. The permissions things is well explained here

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

- basically, within your home directory you can do what you like, but in the rest of the Ubuntu system you have to "give" yourself permission.

It seems like the second install helped get you through the boot option problem, but I'm not sure what the update issue is here. 

Have you tried the update manager, in System/Admin/Update manager? 

It is also worth checking your main repository sources - these are in System/Admin/Software Sources. Enter your password, and then make sure the 4 main entries in the 1st tab are ticked.
Then see what happens.
Please post back if you are still stuck- someone here can always help out.:)

---

