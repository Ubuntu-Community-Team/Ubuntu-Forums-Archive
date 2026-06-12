---
title: "help ...No sound at all"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by cello_911 on 2008-04-17
have installed sucessfully on my dell inspiron 1520 linux mint 4.0 and love it but have no sound whatsoever, just an error message stating no device or no gstreamer installed , please advice me what i need to do to solve this issue..I am a complete beginner and need step by step assistance..
Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
thanks
cello_911

---

### Post by spiderbatdad on 2008-04-17
```
sudo apt-get install linux-backports-modules-`uname -r` 
``` Those are backticks..usually located above the tab key...they are not apostophes.

Run that command in a terminal and input your password. You will not see any response that your password is being input. Just type it in and hit enter.  To open the terminal go Applications>>Accessories>>Terminal.

If the command doesn't work,  look at the output where it says could not find.....2.6.20-14....or whatever number is there. Open Synaptic package manager...System>>Administration>>Synaptic Package manager and search for linux-backports-modules...find the number that matches your number. Check the box and choose mark for installation, then click Apply near the top...Reboot.
Good luck.

---

