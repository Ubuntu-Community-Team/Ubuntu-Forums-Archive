---
title: "Ubuntu bootup crashes after I installed wireless driver"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by AAFNC on 2007-09-03
I installed Ubuntu 7.04 on an old Compaq computer with Windows 98 SE.

Using ndiswrapper, I installed the driver for the D-Link DWL-G510 wireless card.  While trying to configure the wireless, the system crashed.  I am now unable to get Ubuntu running.  Here are the results for various boot-menu selections.

1.) Ubuntu, kernel 2.6.20-15-gneric
The Ubuntu splash screen comes up, the progress bar gets about one-third of the way, then stops.  The Caps-lock and Scroll-lock lights on the keyboard flash on and off.

2.) Ubuntu, kernel 2.6.20-15-generic (recovery mode)
The system stars up, with lots of messages of things being loaded.  Then I get nothing but this message repeated continuosly:
"[xxx.xxxxxx] atkbd.c: Spurious ACK on isa/0060/serio0.  Some program might be trying access hardware directly." (The xxx.xxxxxx are contiually changing digits.)  The Caps-lock and Scroll-lock lights on the keyboard flash on and off.

3.)  Typing "c"
I get a command line console with a "grub>" prompt.

4.) Windows 95/98/Me
Windows starts up and runs.

I would appreciate any suggestions.  I know almost nothing about Unix, so I there is something I need to do on the command line, please give me low level instructions.  Many thanks in advance.

---

### Post by laidback on 2007-09-03
I suspect that a Guru could sort this from the command line or by running a Live CD, I would be tempted to reinstall Ubuntu from scratch and start again. 

I've used the D-Link AirplusDWLG650, it worked straight from the box in 7.04, no ndiswrapper issues. Worth considering.

---

