---
title: "Black screen."
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Strasher on 2007-12-31
Hello again everyone!
Well I finally got ubuntu installed and grub installed.
Grub worked with windows! Yay!
But on to the problem when I try to boot into my ubuntu Via Grub I get a black screen. So i thought "well ok it must be loading" 3 minutes past. Does it really take longer to boot? 
I have a 2ghz processer and 889mb of ram. 
So i don't really think it should take that long.
Any tips?
Thanks,
-Strasher :popcorn:

---

### Post by tgilber1 on 2007-12-31
A blank screen could be caused by missing usplash package, wrong Xorg driver (video driver), Linux getting hung up on a daemon during bootup, etc.  Hence, it is difficult to ascertain what is causing the problem.  Please, could you provide a little more info?

Try booting using the recovery option.  

1.  When you boot up, hit ESC key when GRUB menu countdown starts (default=3 seconds).
2.  Choose the kernel line with the word recovery.  This option will get you to the root prompt.
3.  Post errors, if you get any.  If not, then type exit to continue booting - watch for errors and post.
4.  You can also check the following log files for errors in the /var/log directory - check dmesg, boot, message, and daemon.  Also, check the all the log files in the /var/log/gdm/*.  This directory has the files that log Xorg when starting up.

ex.  "zmore /var/log/gdm/\:0.log" #need to use the escape character backslash \ before colon

---

