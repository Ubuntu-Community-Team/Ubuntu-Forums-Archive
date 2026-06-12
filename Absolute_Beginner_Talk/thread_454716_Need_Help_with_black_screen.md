---
title: "Need Help with black screen"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by kjjw101401 on 2007-05-25
Please help i am new to Ubuntu and everything went fine with the install but after i am on for about 15 min the screen goes black . Any suggestions would be greatly appreciated. I am tired of windows and the problems i constantly have with security and i would love to use Windows as little as possible. Also i am dual booting. Feisty Fawn is the version I am using. I have a ATI Radeon 9250 Video card I have read of others having problems with that card.I have been able to get back to the login screen by pressing ctrl-alt-backspace but i lose what ever i am working on or doing at the time. Not really sure what to look for because this is my first Linux experience. Any guidence in diagnosing the problems would be greatly appreciated

---

### Post by init1 on 2007-05-25
Ok, so you start Ubuntu, and everything is fine until, for no apparent reason, your screen goes black, right? What next? Nothing? It is probably a X server problem. Does this happen when you use the terminal (not emulated, the actual terminal)? Reboot and try selecting one of the grub boot options (might be recovery mode, I don't know). You will login and work in a textual environment. If you do not know how to use this, just wait for those 15 or so minutes. If the screen does not go blank, it is almost definitely a X server problem. I think you may need to edit some settings, but I am not sure.

---

### Post by icechen1 on 2007-05-25
> **kjjw101401 said:**
> Please help i am new to Ubuntu and everything went fine with the install but after i am on for about 15 min the screen goes black . Any suggestions would be greatly appreciated. I am tired of windows and the problems i constantly have with security and i would love to use Windows as little as possible. Also i am dual booting. Feisty Fawn is the version I am using. I have a ATI Radeon 9250 Video card I have read of others having problems with that card.I have been able to get back to the login screen by pressing ctrl-alt-backspace but i lose what ever i am working on or doing at the time. Not really sure what to look for because this is my first Linux experience. Any guidence in diagnosing the problems would be greatly appreciated

did you installed the ati video card driver?

---

### Post by kjjw101401 on 2007-05-25
Ok bare with me. The screen just go black and the monitor says no input. I think i can get into the recovery mode. If i thinking right its what appears to be a command line. Or forgive me for saying this but Like Ms Dos right. If thats the case i can wait the 15 min and see. I'm not sure the difference in terminal or Emulating terminal. I am as green as green can get with Linux but I am very pleased with the GUI and performance of everything in my system I just need to learn.

---

### Post by kjjw101401 on 2007-05-25
I installed it once which did not seem to correct the prob. This is actually my second install of Ubuntu. I though maybe reinstalling it would possibly correct the prob. No such Luck.

---

### Post by init1 on 2007-05-25
Yes, the command line is somewhat like Ms Dos. The commands are different, though. You did exactly what you should have done. A terminal emulator is a program in your GUI that acts like a terminal in that it accepts commands. 
Oh, this is different. Your computer is not sending input to your monitor. Maybe you do need a driver.

---

### Post by kjjw101401 on 2007-05-25
Whats wierd is i can ctrl-alt-backspace and get back to the login screen and the log back in . Same thing happens though after a little bit does the same thing.

---

### Post by jerrylamos on 2007-05-25
Ctrl-Alt-Backspace kills Xwindows so you get back to a command line.  Then what you can try is:
sudo dpkg-reconfigure -phigh xserver-xorg
Note!  There are no blanks before the - except for -phigh.

That gives you a menu driven setup for Xwindows so you can try different things.  I use driver ati although there may be other drivers available.  It also gives you a chance to select screen resolution, use one that works for your graphics chip and monitor.

Then if it looks like it went O.K., do
startx
 
which should get you your desktop back.  Linux Debian and Ubuntu are trying to improve the Xwindows support of various configurations and Feisty does run on one of the computers here that earlier releases didn't, however given the huge variety of monitors and graphics cards out there it can be technically difficult to do.

---

### Post by kjjw101401 on 2007-05-26
Ok I am not at it right now but I'll try to do it and let you know how it goes.

---

### Post by init1 on 2007-05-26
Weird! The fact that your screen says "No Input" suggests that it is not an X issue, but the fact that ctrl+alt+backspace works makes it definitively an X issue. Your X is crashing, but we don't know why. Maybe your resolution is too high, I don't know much about this. In puppy linux, the xorg server would crash for no reason and I would have to switch to vesa. Maybe it  is a similar issue. Maybe you can install vesa.

---

