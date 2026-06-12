---
title: "Shutdown / Boot hang .. Please help"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Jake7482 on 2007-02-24
[SIZE="4"]I am trying linux for the very first time and I am having trouble right from the start. I installed ubuntu 6.10 on my HP Pavilion dv6000 and everything  seems to run fine until I try to shutdown the system. As soon as I click shutdown, the screen goes black and the system hangs with a note from the shutdown music playing continusously. I have to force shutdown and when I try to start the ststem back up, I only make it to just after the splash screen and progress bar. After the progress bar makes it to the end the screen goes black and the computer is lifeless. I do not see any error messages and pressing “ESC” does nothing. I have reinstalled a couple of times only to be confronted by the same problem when I try to shut the system down. I do not know how to fix ubuntu so that it will start back up without reinstalling or, how to fix the shutdown problem..Any help would be very much appreciated. :confused: [/SIZE]

---

### Post by chggr on 2007-02-24
Next time, try to shut down using one of your terminals. Press simultaneously ctrl + alt + F2. This will get to to a terminal where you can type in your username and password. Then issue the command:

sudo halt

This command will shut down your computer. See if the same problems occur again. If they do, then you can reinstall Ubuntu using the alternate LiveCD.

PS. If you want from a terminal to get back to your Graphical Interface, just press ctrl + alt+  F7.

---

### Post by teaker1s on 2007-03-03
known issue look here for further guidance or reply on thread and I'll suggest fix(s)
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")

---

