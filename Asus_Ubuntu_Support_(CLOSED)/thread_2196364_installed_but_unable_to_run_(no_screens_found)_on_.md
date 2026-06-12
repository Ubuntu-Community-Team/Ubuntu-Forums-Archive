---
title: "installed but unable to run (no screens found) on touchscreen netbook (x102b)"
date: 2013-12-29
forum: Asus Ubuntu Support (CLOSED)
---

### Post by alanholpin2 on 2013-12-29
Can anybody help please - I  have been trying to help a friend who finds his windows 8 touchscreen net-book unusable, but for the first time I have not been able to do a successful installation. I am not technical but have been using ubuntu for 5 years now.
On running from the live usb there was a 'low graphics mode' warning, but it would not get to a desktop at all - not even in low graphics mode. I tried all the options I was given, but to no success. I have posted the x-log file (i think that's what it is!) here:
[https://plus.google.com/107351332097366363159/posts/BEvbszV22XH](https://plus.google.com/107351332097366363159/posts/BEvbszV22XH) 

However I discovered that if I selected the install option from the usb menu, it took me to a perfectly rendered installation screen from where I was able to partition the drive and successfully install the system- and yet on rebooting into the new installion there is the same low graphics mode error and I am unable to get into the desktop.

Is this something for which there is a workaround to or will we have to wait for a kernel update or something?

I also tried with other distros and various versions back to 12.04 all with the same result.

Thanks in advance for any help!





[INDENT]

[/INDENT]

---

### Post by alanholpin2 on 2013-12-30
Solved this with the following;

Only for ATI graphics cards

When the message that "your system is running in low-graphics mode" appears:
Press Ctrl+Alt+F1 to see the terminal one. Then login with your credentials, and then run the following commands:

sudo apt-get install fglrx    
sudo reboot
The same can be done from the recovery mode (after enabling networking), if your Ubuntu completly refuses to enter anything but recovery mode

---

### Post by Marie_Chevrier on 2013-12-31
I got the exact same problem, but with an AMD graphic card. Any ideas?

---

