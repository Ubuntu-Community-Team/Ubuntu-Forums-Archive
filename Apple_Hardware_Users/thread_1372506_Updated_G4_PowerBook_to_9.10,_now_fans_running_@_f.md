---
title: "Updated G4 PowerBook to 9.10, now fans running @ full tilt!"
date: 2010-01-04
forum: Apple Hardware Users
---

### Post by sean.d on 2010-01-04
I updated my 1.33GHz G4 PowerBook (17") to 9.10, and now it's fans run at full speed, constantly.  Is there a fix for this?  It's quite annoying.

---

### Post by linuxopjemac on 2010-01-05
I found something on the fedora forums for you, which you can try...

> Found a hack to fix the problem
the problem centers around the temperature threshold at which the Linux kernel is instructing the G4 laptop to turn on the CPU fan to cool the CPU down
You can increase the threshold by 5C ... 5 degrees celsius in real time

```
echo 5 > /sys/devices/temperatures/limit_adjust
```

note the fan will kick in when you compile code or other CPU intensive activities

you can add the above string to /etc/rc.local
so that after the system fires up the temp threshold is increased

original article [here]("http://www.fedoraforum.org/forum/showthread.php?t=61014")

Please let us know if it works.

You can also disable the module therm* in /etc/modules. This can be risky though, at your own risk, as then the fan will not kick in at all

---

### Post by sean.d on 2010-01-05
EDIT: Found it.  Do i just add that line to the bottom of the file?

If so... it hasn't worked.


EDIT again: Got it.  's working now.  I disabled the Therm* module, and the fans **returned to their normal behavior**! That is, they no longer run full tilt all the dammed time, and instead come on only as needed, as the systems' temp rises.

---

### Post by linuxopjemac on 2010-01-06
Great news for all those G4 PPC laptop users....I will immediately post on my own website.

see here:
[http://mac.linux.be/content/fans-running-full-speed-g4-laptops](http://mac.linux.be/content/fans-running-full-speed-g4-laptops)

---

### Post by spizo on 2010-02-15
I apologize if this is an obvious thing - but I'm still a bit of a n00b here.
I'm having the same issue and so I tried to make this change but the powers that be won't let me - I'm told I don't have permission to make this change. I've tried to literally change the file as well as making the change via the terminal - in both cases I'm blocked - don't have permission.  How can I get around this? I've tried 'sudo' but also had no luck, though maybe I'm doing that wrong.

thanks

---

### Post by linuxopjemac on 2010-02-15
you have to be root to do this, if you didn't set a root password do the following:

```
sudo passwd
```

and set the root's password (this is the administrator who can change everything in a Linux environment)

then you either login as root:
```
su
```

or you stay as normal user and issue a temporary root command with sudo

```
sudo nano /etc/modules
```

now put a # before therm* and then a CTRL-x and "y" to save.

reboot and it should work

---

### Post by spizo on 2010-02-16
thanks, this worked.
however when I tried to reboot the computer got hung up on this:
* Asking all remaining processes to terminate...

I waited quite a while, tried ctrl+alt+F7, nothing, tried ctrl+alt+delete, nothing... so I had to force it off. After I booted back up again all was fine. I can now reboot no problem. Should I be worried about that message? Is that normal? Also, now that I've bypassed therm* will my fan never come on? Or will it function as it should?

sorry if I'm being paranoid... I spent the whole day reformatting/partitioning/etc after messing things up beyond repair, so I'm being extra cautious now.

thanks again.

---

### Post by linuxopjemac on 2010-02-17
I am not sure whether they don't kick in at all. I would try lm-sensors and carefully look what happens. If you are compiling or playing video for a while, keep an eye on the CPU temperature. If it gets to a point where fans should kick in, and it does not happen, ttop the activities on your computer yourself. If you think it's safe after experimenting, let us know. I have not heard of any problems with this fix though.

[http://www.lm-sensors.org/](http://www.lm-sensors.org/)

---

### Post by spizo on 2010-02-22
thanks, its working. The fans do kick in, just no where near as intensely as before - but it would appear that they don't need to.

thanks again!

---

### Post by linuxopjemac on 2010-02-23
great news again! This fix is safe then.

---

### Post by heluani on 2010-02-23
> **linuxopjemac said:**
> great news again! This fix is safe then.

I woudn't advice for removing the thermal management modules (specially if it's adt746x ) g4s are known to run hot and the hardware limit is too high. The original advice of increasing the limit_adjust parameter is better at least. You should take a look at which version of the module you were running. Take a look at [http://patchwork.kernel.org/patch/63806/](http://patchwork.kernel.org/patch/63806/) On a fresh install of gentoo last week on a powerbook g4 I pulled a kernel that didn't have that patch, so the fans were running at full speed when the cpu was idle and not running at all when I was compiling. Perhaps this was the issue you were experiencing.

By the way, if you have the term_adt746x module running (with the right patch or a newer version) then you should ```
 echo 2 | sudo /sys/devices/temperatures/limit_adjust 
``` replace 2 by 5 at your own risk (this is what Apple does though).

R.

---

