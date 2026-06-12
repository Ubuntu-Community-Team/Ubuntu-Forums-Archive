---
title: "no login splash screen"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by mummra1 on 2007-11-17
I'm running Kubuntu 7.10.  I'm having a strange problem that happens when I do a normal bootup.  Instead of going to the login splash screen, I get a black screen with text saying 'Log in on tty6', and I'm prompted for my login and password.  I am then logged into the system, but the xsession doesn't seem to have started, b/c there is no desktop, just a cursor.   However, if I boot into recovery  mode, then do an init 3, it boots up the rest of the way just fine and I can log in as normal.:confused:   Seems like something wrong with X server but I'm not really sure...

---

### Post by aysiu on 2007-11-17
I don't know why it would give you tty6 (if X is broken somehow, it usually defaults to tty1).

Press Control-Alt-F1 (this should get you tty1). Log in and type ```
sudo /etc/init.d/kdm restart
``` and see if that helps.

---

### Post by mummra1 on 2007-11-17
Right. The strange thing is that when I do init 6 to reboot, it says 'kdm shutting down', meaning that it already had started.  I did try restarting kdm but to no avail...

...but I will try again anyway.

---

