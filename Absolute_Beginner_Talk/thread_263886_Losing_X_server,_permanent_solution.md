---
title: "Losing X server, permanent solution?"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by geercom on 2006-09-23
I had Ubuntu loaded and working fine. Then, it said it couldn't start the X server (no ubuntu gui) and that it had to be repaired.

Though the computer obviously does a POST test no problem, there were problems with the computer when using Windows 98se, which had worked fine on this computer until recently.

The computer hadn't been dusted out in a while (was not origianlly mine) so I took care of that. I am reloading Ubuntu now.

What in hardware or software might have caused the X server to stop working? Is there a diagnostic utility in Ubuntu that can tell me something about whether it might be a hardware problem, even though the computer boots OK?

I'm thinking maybe it's the hdd having unrecoverable sectors. Is there an Ubuntu or Ubuntu compatible Linux tool comparable to MS DOS Scan Disk that can ID and then make sure unrecoverable, dead sectors are not used?

Also, the machine has 256MB RAM, 10GB HDD space and a 798GHz CPU, so I believe it meets or exceeds all required specs to use Ubuntu  6.06, which is what I have here.

And leads, answers?

---

### Post by ewl1217 on 2006-09-23
The hardware sounds good enough to run Ubuntu, but it may be a little slow depending on what you're doing. That aside, it's probably an issue with the video card. Log in, then try running the following command:
```
sudo /etc/init.d/gdm start
```
If that works, then we're done, but if it doesn't, post the output it gives here.

**EDIT:** From my understanding of the problem, the normal screen isn't coming up, you're given an error message, and then you get taken to a text-based login screen. If that isn't the case, then disregard my post.

---

### Post by geercom on 2006-09-23
I got an option to either read output to diagnose or an error message. I reloaded the OS. GNOME Display Manager opens OK.

What should I check if it happens again?

---

### Post by bulldog on 2006-09-24
Did you do a kernel update?

Which kernel are you running?

Do you have the same problem with the previous kernel?

---

### Post by geercom on 2006-09-24
No kernel update. How do I find out which kernel I'm running? How do I update the kernel?

---

### Post by bulldog on 2006-09-24
> **geercom said:**
> No kernel update. How do I find out which kernel I'm running? How do I update the kernel?

Type in terminal

uname -r   

for your current kernel

Type in terminal

cat /boot/grub/menu.lst

To see which kernels are available for boot.

---

### Post by geercom on 2006-09-24
Current kernel is 2.6.15-23-386

Available kernels include this one, this one in recovery mode and something called memtest. Is there a newer kernel? Should I get it? Where and how do I get it?

---

### Post by bulldog on 2006-09-24
If there's a newer kernel available you get it by the little orange box which provide you with the updates.

You could do,if you wish,

sudo aptitude update 
sudo aptitude upgrade

to see if there is an update for your computer.

---

### Post by bulldog on 2006-09-24
But this is not related with your problem.

It could be however that a kernel update got you the X-server malfunction.

Did you install drivers for your graphical card allready?
It's adviced to do so there is Automatix a utility that can provide you with a lot of multimedia stuff,java and much more.

[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

---

