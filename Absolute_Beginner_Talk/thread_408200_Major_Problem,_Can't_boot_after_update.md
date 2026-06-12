---
title: "Major Problem, Can't boot after update"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by slkuhn on 2007-04-13
Hi everyone, 
I just installed some updates tonight and I was told I need to restart. When I restarted Ubuntu (Feisty), the progress bar wouldnt even start, let alone advance. ?? I think an error in the updates might have damaged a critical file?? 
I have created a small partition with edgy on it and I have mounted my Feisty partition.
Will there be a log file hidden somewhere on my Feisty filesystem that might tell me whats wrong? I realize that I dont have specifics and that it could be about 1.2 million different things. If anyone could give me some guidance I would much appreciate it.

-slk

---

### Post by tonyr1988 on 2007-04-13
In your Grub menu, are there multiple kernel numbers listed? If so, try an older one (smaller number) and see if that works.

Are you using proprietary graphics drivers (or any drivers for that matter)? You should get past the loading bar, but you never know....

---

### Post by nike984 on 2007-04-13
similar problem has been reported.
There is a temporarily  solution  in  this  post (page 3)
[http://ubuntuforums.org/showthread.php?t=408057](http://ubuntuforums.org/showthread.php?t=408057)

=================================================
OK, guys... for people with the same problem I had, I have found a solution.

I'll edit this post in a minute and tell you what I did to temporarily solve this problem, so don't despair yet.

Here it goes.

Go grab yourselves some sort of Live CD, anything with which you can access your Ubuntu partition with read & write acess (I used Damn Small, for instance)

The really simple solution for now is to replace your **initrd.img-2.6.20-14-386** which is located in the **/boot** folder with the one that's marked as **initrd.img-2.6.20-14-386.*bak*** (the backup you replaced with the earlier upgrade).

Try booting into Ubuntu then, and... voilá. You're back :wink:

So, for the time being, and at least while you know it's not safe to upgrade, hold your trigger-happy littles finger, make a backup of the good **initrd.img-2.6.20-14-386** and keep it for when you do venture into trying to upgrade again. *relief sigh*
================================================

---

