---
title: "[SOLVED] error during installing of i386 package"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Durden10 on 2007-07-10
Hi

I'm trying to install a i386.deb package, but I'm always getting an error message "Cant open more than one application for software management at a time", even when I close all related applications...
Thanks,
Joe

---

### Post by AlexenderReez on 2007-07-10
are you open synaptic at the same time try to install package using double click(deb package manager) ?try to restart ......

---

### Post by Chilli Bob on 2007-07-10
If the update manager is open while trying to install a package, you will get this error too.

---

### Post by Durden10 on 2007-07-10
Well I closed all the related programs, rebooted, but it still doesnt work...

Is there any other way to install this kind of application? Without an automatic installer?

---

### Post by Malibu Illusion on 2007-07-10
If you're absolutely sure there is nothing that should be causing this:

```
sudo rm /var/lib/dpkg/lock
```

Then try installing.

---

### Post by Durden10 on 2007-07-10
Sorry, but why should I do this? Erasing a file doesnt seem to be a logic solution for this problem

---

### Post by Malibu Illusion on 2007-07-10
This particular file is responsible for ensuring that only one package management application is running at a time; dpkg checks this file and attempts to see if it has exclusive rights over it to determine this.

It is possible that there is a problem with this file causing the error you're seeing.  By deleting it, a fresh lock file will be created which may resolve your problem.

Either way, whether it resolves the issue or not, all you're doing is deleting a 0 byte file that recreates itself, nothing system-critical.  It is worth trying.

---

### Post by UnixAnt on 2007-07-10
If you are comfortable using the console, try the following:

$ ps -ef | egrep -i "synaptic|apt|dpkg"

This will (hopefully) show you how many instances of package management apps you are running.

Start with synaptic, if there are multiple instances resident then kill them off with the following:

$ kill $Process_ID_of_synaptic

Perform a ps -ef as above to ensure there are no more running, then try installing again.

---

### Post by Durden10 on 2007-07-10
Ok, I tried out the 2 techniques, unfortunately none of them helped. In addition to that I encountered another problem; whenever I try to run Synaptics I get 
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."
Even after reboot...

---

### Post by Malibu Illusion on 2007-07-10
Rebooting is a Windows technique, it'll seldom help under Linux.  Execute:

```
dpkg --configure -a
```

---

### Post by schorsch on 2007-07-10
```
sudo dpkg --configure -a
```

---

### Post by Durden10 on 2007-07-11
I just resolved my problem; the reason for it was an interrupted installation of a package. After manually deleting it, nautilus started working again.:guitar:

---

