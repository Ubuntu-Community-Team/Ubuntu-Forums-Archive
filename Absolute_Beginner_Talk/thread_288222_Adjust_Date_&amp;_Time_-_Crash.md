---
title: "Adjust Date &amp; Time - Crash"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Dr.Maggot on 2006-10-29
I'm pretty new to Ubuntu but successfully applied the 6.06 to 6.10 upgrade to two systems (one was a Win2K dual boot) and a new installation (also a Win 2K dual boot).  

The fourth was an upgrade from 6.06 to 6.10 but with the following problem:  When I right-click on the clock in the panel to adjust the date and the time and to set the NTP server reference clock, I get a crash applet reporting to [http://bugzilla.gnome.org/show_bug.cgi?id=366838](http://bugzilla.gnome.org/show_bug.cgi?id=366838)

Their comment was: *"This issue has been fixed already, please install any updates provided by Ubuntu."*

I'm at a loss as to how to troubleshoot this as it seems my software status is currently "up to date."

Any suggestions will be greatly appreciated.

Mike

---

### Post by Bajo_sk on 2006-10-29
I have this problem too

---

### Post by tzulberti on 2006-10-29
I have this problem too..... Maybe they solved for gnome, but yet they have not done an update for Ubuntu...

---

### Post by richardq on 2006-10-29
Same problem here. I filed a similar bug (with similar response). Since we just changed underwent a 1 hour time change it's pretty important to me. I ended up rebooting and hitting F2 to enter the BIOS settings and made the time modification there. Seems to work.

---

### Post by Dual Cortex on 2006-10-29
[http://bugzilla.gnome.org/show_bug.cgi?id=351603#c11](http://bugzilla.gnome.org/show_bug.cgi?id=351603#c11)
"I'm getting the same stacktrace with time-admin from ubuntu packages when it
isn't able to communicate with gnome-screensaver, this issue is already fixed
in CVS HEAD and will be available in the next g-s-t release. Thanks for the bug
report!"

That was posted on August 30 ...

---

### Post by jd65pl on 2006-10-29
The servers are busy at the moment, you may have to wait for a while until the servers calm down a little. Have you all done....

```
sudo aptitude update
```

---

### Post by Dr.Maggot on 2006-10-30
> **jd65pl said:**
> The servers are busy at the moment, you may have to wait for a while until the servers calm down a little. Have you all done....

```
sudo aptitude update
```
yes, but no change.

thanks,

Mike

---

### Post by kitman420 on 2006-10-30
same problem here. i'm running ubuntu edgy on my macbook pro with parallels.
no changes after
```
sudo apt-get update
```
```
sudo apt-get install gnome-system-tools
```

---

