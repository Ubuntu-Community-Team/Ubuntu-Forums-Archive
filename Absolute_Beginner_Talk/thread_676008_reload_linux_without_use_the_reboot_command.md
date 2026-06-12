---
title: "reload linux without use the reboot command"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by herbert tamayo on 2008-01-23
Hi, I made a change in the configuration file of tomcat5 and also in the .bashrc, to try these changes I reboot the computer (using the reboot command),my question is:

is there a way to reload linux without use the reboot command? I mean, I don't need to pass again the POST process and then GRUB and then go on ubuntu, I just want to go to process of init ubuntu, so, is this possible?

thanks

---

### Post by waffen on 2008-01-23
uhm.,... why you dont restart the tomcat process?? Ubuntu is a Linux not win.. :)

---

### Post by Nano Geek on 2008-01-23
Running **sudo /etc/init.d/<name_of_program> restart** will restart the program without having to reboot your computer.

---

### Post by dannyboy79 on 2008-01-23
don't know what tomcat5 is but you shoudl just be able to close that app and open it again if it's not a process. a process is controlled by init.d and the last poster has already informed you how to reload config files for init.d ran processes. as far the bash settings, they should take effect the next time you start up a terminal. if all else fails, try 
ctrl-alt-backspace
that restarts X and maybe even all teh processes without resetting the bios, computer etc etc.

---

