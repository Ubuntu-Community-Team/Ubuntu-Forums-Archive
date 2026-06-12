---
title: "Oops! - There was an error starting the GNOME Settings Daemon."
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Gigidy5 on 2008-02-10
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.




I looked at the other posts and none applied to me, or had answers.


What do I do?!?!?


i have gutsy gibbon  7.10
thanks

---

### Post by freesitebuilder on 2008-02-11
I'm having this too - found some stuff by googling
Launchpad bug report [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946)

another thread here:
[http://ubuntuforums.org/showthread.php?p=3664438](http://ubuntuforums.org/showthread.php?p=3664438)

---

### Post by louieb on 2008-02-11
Odd isn't it? I get that message every now and then after a reboot.  I just reboot my PC again and the message goes away and everything works fine.

---

### Post by Joeb454 on 2008-02-11
> **louieb said:**
> I just reboot my PC and the message goes away and everything works fine.

That's exactly what I do. It's only ever happened to me once though, and I've had Ubuntu 7.10 installed on this machine since November. I always seem to get it on the LiveCD as well...it gets quite annoying.

---

### Post by ThrobbingBrain66 on 2008-02-11
> **Gigidy5 said:**
> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.




I looked at the other posts and none applied to me, or had answers.


What do I do?!?!?


i have gutsy gibbon  7.10
thanks

To fix it until your next reboot, open the Run Application dialog (Alt+F2), type *gnome-settings-daemon* in the box and hit enter.

---

### Post by tritops on 2008-02-15
Hi there, newbie here.

I get this problem as well, ,but the only time it happens is when I start from cold boot.  
Once I click ok to it and then log-off/log-on/restart, the problem does not recur til my next cold boot.  

The thing i notice is that my wifi usb adapter is not set to start automatically.
not quite sure why this behaviour exist...

:confused:

---

