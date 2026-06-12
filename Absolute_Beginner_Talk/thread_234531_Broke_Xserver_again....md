---
title: "Broke Xserver again..."
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by Tom Brokaw on 2006-08-11
I was trying to configure my Logitech mouse and edited my xorg.conf.  Did something wrong and after a reboot, I get a quick flash of the Nvidia boot screen and then (so far) one of two things: a black screen, or a white screen with black dashes on it.

I booted into the recovery mode from grub, but it's asking me for my "root" password, not my sudo password.  I searched on here because I know I've seen something similar but can't find it.  Here's what the prompt says:

root@username-Ubuntu:~#

Where do I go from here?

Thanks!

[edit] Messing around, typed "login" and then my regular login information...

---

### Post by spd106 on 2006-08-11
Did you not make a backup copy[-X 

You could always try **dpkg-reconfigure xserver-xorg**
It's always worth keeping a copy of a critical file such as this ( cp -v xorg.conf xorg.conf.old )

---

### Post by r4ik on 2006-08-11
Please boot the normal way and do a Ctrl Alt F1 to get to the CLI.

sudo dpkg-reconfigure xserver-xorg

should do it.

Good luck !

---

### Post by Jussi Kukkonen on 2006-08-11
It's not asking you for a password, it's a shell prompt (you are root already). Just do *nano /etc/X11/xorg.conf*

Many people do not realise that without setting bootloader passwords their computer is wide open to anyone without any passwords. Of course, if an intruder has physical access, you're screwed anyway but at least grub passwords prevent passers-by from logging in as root...

---

### Post by Tom Brokaw on 2006-08-11
I did make a backup copy.  My problem was that I could not get to a CLI that I could use, ie, I didn't realize that at the prompt I noted above, I had to type "login" and then enter my username and pw.

I did that, and then tried to restore xorg.conf file via this code:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-logi
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

Then I entered ```
sudo /etc/init.d/gdm restart
```

I an error that says something about the power bus, and it seemed like the computer was going to lock up, but I was able to reboot and now it seems like all is OK, or at least back to square one.

Figures, right after I get frustrated enough to ask for help, I figure it out...  Thanks for the quick replies, though!

---

