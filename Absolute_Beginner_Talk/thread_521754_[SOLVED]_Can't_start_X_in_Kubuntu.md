---
title: "[SOLVED] Can't start X in Kubuntu"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by therandman on 2007-08-09
Okay, so I had my original login name set to randmanmain since I have multiple computers.  I decded to change my name in system settings to randman, but didn't do anything else.  Stupid me, I restarted X (control-alt-backspace) and tried to login as randman, and now it's coming up with errors.  It is trying to access and write to configuration files in my randman folder, but everything is in my randmanmain folder.  How do I change my user name back so I can login to X?  Thanks!

---

### Post by aysiu on 2007-08-09
So you're stuck at the command prompt?

I would do this:

**Step 1**
Reboot and select recovery mode (the boot option right below the usual one). This will log you in as root.

**Step 2** ```
adduser recoveryrand
adduser recoveryrand admin
reboot
```

**Step 3**
Boot into regular mode. If X loads, log in as *recoveryrand* and try to repair the damage with System Settings. If X doesn't load, log in as *recoveryrand* and type ```
sudo /etc/init.d/kdm start
```

---

### Post by therandman on 2007-08-09
Thanks aysiu!  Worked perfectly!  So how do I change my username correctly so I don't break anything?  Also, do I just delete the recoveryrand?  Thanks again for your help!

---

### Post by aysiu on 2007-08-09
I wouldn't delete *recoveryrand* until you know *randmanmain* is working again.

I don't know how to change the username correctly. Can you use System Settings to just undo what you did before?

---

### Post by therandman on 2007-08-09
I was able to get in and change back what I had changed.  I also re-rebooted just to make sure it is still working, so I will delete the recovery.  Thanks again!

---

