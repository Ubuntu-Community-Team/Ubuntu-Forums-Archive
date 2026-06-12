---
title: "Ubuntu won't start after I mounted /home to separate partition"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2006-07-13
I tried mounting /home to a separate partition using a line I got from a thread here and added it to /etc/fstab
(/dev/sda6       /home           ext3    defaults        0       2)
This line was probably right, because I first got the message that my users directory didn't exist, and then when I created a directory in that partition (from Windows) with my username, I did not get that error any more.
But still:
"user's $HOME/ .dmrc file is being ignored. This prevents the default session and language from being saved...." and sth about 644 rights.
What went wrong, and can I get it to work again?

---

### Post by Ragazzo on 2006-07-13
Are you sure your partition type is Ext3 because Windows can't read/write it without using third party software? And when do you get this error (booting?) and what happens after that?

---

### Post by aysiu on 2006-07-13
Do you have a live CD?

Or, if not, can you boot into recovery mode?

---

### Post by 1002285 on 2006-07-13
Yes, it is ext3 and I have installed a driver in Windows for accessing it.
I do have a live CD and I can boot into recovery mode, but I don't really know what I should do there.
And I got this errot after inserting my user name and password. After that it says sth like "your session lasted less than 10 seconds".
I have tried to copy all the files from my previous home directory to the place I made it to be now, but sth didn't let me do that - I got some directories to the new place, but then one file could not be moved.

---

### Post by aysiu on 2006-07-13
Copying the home directory is a bit tricky and can't just be done by copy and paste. See this for more details:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by 1002285 on 2006-07-14
OK, maybe this was a solution for a dumb person, but I just started a new install of Dapper. I didn't have anything important in the /home directory anyway, everything was already backed up to another computer.
As the partition that I wanted to make /home was empty already, it went very easily.
Thanks for the help.

---

