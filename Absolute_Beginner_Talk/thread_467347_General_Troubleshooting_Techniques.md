---
title: "General Troubleshooting Techniques"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by captlogic on 2007-06-07
OK, I'm totally new to linux, but I'm a seasoned Windows pro.

I've got feisty installed, with dual boot - no problems.
I've got my widescreen lcd working - a few problems, but got them solved.
I've got my 5.1 speaker setup working - sorta' (still working on this one)
I've got some of the apps from automatix installed, beryl WAS working just fine on the nvidia restricted drivers.

and then I broke something.(I don't what) (I don't know how either).
Beryl loads, but my animations stopped working.
Then I noticed that deluge stopped working (Click on the menu item for it and the 'taskbar' icon appears and then goes away and Deluge is not running :(  )

I'm more than willing to put in some head-banging-config-file-edititng-log searching-problem-solving, the problem is I don't even know where to begin in the linux world?

(I've tried re-installing beryl, that didn't help)

Where do I begin, what are the relevant log files?

HELP HELP HELP - PLEASE PLEASE PLEASE   THANKS THANKS THANKS

---

### Post by NeoLithium on 2007-06-07
Usually you can see any error messages by opening up a terminal and typing the name of the program to run, it will run it and if it quits, the terminal will take the spit out of what happened.  Perhaps some of that can be useful.

---

### Post by nick_h on 2007-06-07
You can view the log files from System -> Administration -> System Log

From a terminal you can find the logs in /var/log

View them with commands like:

less syslog
cat Xorg.0.log | grep nvidia

---

### Post by captlogic on 2007-06-11
> **NeoLithium said:**
> Usually you can see any error messages by opening up a terminal and typing the name of the program to run, it will run it and if it quits, the terminal will take the spit out of what happened.  Perhaps some of that can be useful.

Running deluge from the terminal gave me the error message I needed and I got the problem solved, thanks.


For others I found the solution in this thread 
[http://ubuntuforums.org/showthread.php?t=383420](http://ubuntuforums.org/showthread.php?t=383420)

Thanks again.

---

