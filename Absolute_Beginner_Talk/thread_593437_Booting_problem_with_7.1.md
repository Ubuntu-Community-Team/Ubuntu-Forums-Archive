---
title: "Booting problem with 7.1"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by James Fitzpatrick on 2007-10-27
I just tried to update my system to 7.1, and now my computer won't boot.  After downloading and installing the upgrade, I restarted the system, and the first thing I noticed was that my screen resolution had changed.  I tried to correct this, but a message said I had to log off.  I restarted, and the system seemed to have begun booting, but then it just stopped.  I tried restarting several times, but the behavior was the same.
I thought I might try the recovery mode (I've never done this before), but I get to the point where it says, "root@fawn:~#"  and I don't know what to do.  What command do I enter?

---

### Post by overdrank on 2007-10-28
> **James Fitzpatrick said:**
> I just tried to update my system to 7.1, and now my computer won't boot.  After downloading and installing the upgrade, I restarted the system, and the first thing I noticed was that my screen resolution had changed.  I tried to correct this, but a message said I had to log off.  I restarted, and the system seemed to have begun booting, but then it just stopped.  I tried restarting several times, but the behavior was the same.
I thought I might try the recovery mode (I've never done this before), but I get to the point where it says, "root@fawn:~#"  and I don't know what to do.  What command do I enter?

Hi you can try and reconfigure you xorg from the recovery mode and maybe this will help
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Good luck!

---

### Post by James Fitzpatrick on 2007-10-29
Thank you.  I have tried this and I get this response:
xserver -xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/x11/xorg.conf.20071029010619

Then it comes back to root@fawn:~#

---

### Post by sochbat on 2007-10-29
Give this a shot.  Worked well for me.

sudo dpkg-reconfigure xserver-xorg

Helps get your graphic interface back, in a simple way.  Maybe not the best yet, but it'll get you to where you need to be.

---

### Post by jaybombalous on 2007-10-29
then reboot and see what happens. If you get the command enter line again without any errors or warnings then u have accomplished something.


the warning in this case is telling u its overwriting a possible configuration file (reconfig means reset to default in this case like if the package was just installed and never altered) and its backing it up in that path. Which isn't a bad thing, then u can go back and compare to see maybe what u did wrong if anything.

---

### Post by James Fitzpatrick on 2007-10-29
Ah, wait!  I just rebooted and I'm back in business!  Thank you!

---

