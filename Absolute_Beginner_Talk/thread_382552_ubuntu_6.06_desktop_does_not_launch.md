---
title: "ubuntu 6.06 desktop does not launch"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by oceanmame on 2007-03-12
Definitely a newbie, but followed the instructions and managed to download the 6.06 iso, burn it onto a cd using infa recorder (cd 4x), and launch the desktop a few times off of the cd. I then installed a new anti-virus software, and now the desktop does not launch. I do not know if/why the installation of the software would cause the problem. 

The boot menu comes up fine and the diagnostics come up on the splash screen. Then the screen turns reddish brown and that is it; the desktop no longer appears and the system is frozen. When I do a hard reset, ubuntu exits fine, the cd pops out, and the system shuts off.

I read other posts where the poster was able to provide error messages. However, I cannot or did not see any.

I am using an HP pavilion a245c: AMD Athlon XP processor, 512 MB ddr sdram, 120 GB hard drive, nvidia geforce 4mx. 

Thank you for your help.

---

### Post by ianhaycox on 2007-03-12
Try hitting Ctrl-Alt-F8 at your brown screen. It should give you a text screen. Are there any messages there ? Press Ctrl-Alt-F7 to get back to the brown screen.

Alternatively press Ctrl-Alt-F1 and you should be presented with a login: prompt so you can login and do some investigation from the command line.

Possibly try restarting the X Server via Ctrl-Alt-Backspace, and watch for errors.

---

### Post by oceanmame on 2007-03-13
Ian,

Thank you very much for your reply. I was finally able to run your suggestions.

Cntl-Alt-F8: no error message. The last three entries were:
Starting periodic command schedule        OK
Checking battery state                          OK
Running local root scripts (/etc/rc.local)    OK

Cntl-Alt-F1: I did not have to login and was able to run more /etc/rc.local - the only uncommented statement was exit 0

Cntl-Alt-Backspace: A yellow screen appeared which said user Ubuntu will login in 10 seconds. Then the red-brown screen returns. On the yellow screen, there is an option button at the bottom of the screen, and I was able to select restart, rather than the hard reboot to exit Ubuntu.

Cntl-Alt-F8 after the Cntl-Alt-Backspace: no error message and the last three entries are the same as above.

I was curious if the other flavors of Ubuntu 6.06 would work, so I downloaded the Kubuntu iso, and the kubuntu desktop comes up. Very strange that ubuntu does not.

Thank you for your help.

---

