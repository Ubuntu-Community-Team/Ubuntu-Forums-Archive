---
title: "xorg.corf"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by highstead on 2008-01-20
I've been playing with Ubuntu for aw hile now but every time i have to go edit the xorg.conf file everything gets shot to hell.  I recently tweaked my mouse settings being careful to follow the tutorial in order to get the thumb buttons working, however in doing so i managed to screw up the dispaly when restarting X.

Long story short if you didn't read that.  Followed this thread: [http://ubuntuforums.org/showthread.php?t=65471](http://ubuntuforums.org/showthread.php?t=65471) 
And when i do, xorg.conf screws up in a unexpected way.  It runs in low resolution mode, which my monitors don't support (running twinView).

Questions: 
- is it possible X is using a different xorg.conf?
- the does [this]("http://ubuntuforums.org/showthread.php?p=4169381#post4169381") seem to be missing anything?

Any help would be appreciated will post the xorg.conf on request.

---

### Post by blueridgedog on 2008-01-20
Some generic advice:

Always make a back of your xorg.conf file before editing.

If you ONLY commented out your existing InputDevice section and added the new one from the link you provided, then I can't see a way to have impacted your resolution, unless you have left a section or endsection tag out or uncommented.

There should be only one config file, /etc/X11/xorg.conf.

---

### Post by tgilber1 on 2008-01-20
Yes, the system can revert to another xorg.conf file.  In the event, there is something wrong with the main xorg.conf file, you system may boot up to the backup file called xorg.conf.failsafe.  Check out the gdm.conf in the /etc/gdm directory.  Look for the lines

# This runs Ubuntu's BulletProof-X failsafe mode.
FailsafeXServer=/etc/gdm/failsafeXServer

If you want to make sure that it does not boot up to failsafe mode, comment the line out.  Then, restart the XServer with the following line "/etc/init.d/gdm restart" and check your /var/log/Xorg.0.log file for errors to see what exactly is causing your problem.

---

