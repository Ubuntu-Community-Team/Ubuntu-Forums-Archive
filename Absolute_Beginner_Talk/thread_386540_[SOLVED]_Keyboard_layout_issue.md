---
title: "[SOLVED] Keyboard layout issue"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by jamoo1980 on 2007-03-17
Hello all

I've seen a few variations on this problem in forums, but haven't found a solution yet. I wonder if anyone can help...

I'm running Ubuntu 6.06 (Dapper Drake) on my Toshiba Portege laptop. It works brilliantly apart from one tiny - but very annoying - problem! After logging in, the keyboard changes to QWERTZ layout. The only way I've found to rectify this is to go in to the Keyboard Layout settings and choose "Generic 101 key". But I have to do this every time after logging in. The Generic 101 key setting will still be there, but layout will behave as QWERTZ, so the next time, I have to swap to Generic 104 key, and keep on alternating between the two after every log in! Strangely, the keyboard layout is correct at the login screen; it's just after login that it seems to change...

I'm posting this in the absolute beginners forum as I'm not yet completely familiar with the way the file system is organised in Linux. Basically, I'm fine with editing config files and command line stuff etc, I'm just not always sure where to find the various config files!

Any help, bearing this in mind, would be greatly appreciated :)

Thanks!
James

---

### Post by mrmonday on 2007-03-17
I think there is an option in the xorg.conf file for changing the keyboard layout.
```
sudo gedit /etc/x11/xorg.conf
```
Can you copy and paste the output?

EDIT: If someone knows the correct way of doing that, could they tell me? I know that works, but I'm sure there is a better way

---

### Post by jamoo1980 on 2008-01-27
...well shortly afterwards I upgraded to 7.04, then 7.10, and I never had this keyboard problem again...

---

### Post by fela on 2008-04-09
> **mrmonday said:**
> I think there is an option in the xorg.conf file for changing the keyboard layout.
```
sudo gedit /etc/x11/xorg.conf
```
Can you copy and paste the output?

EDIT: If someone knows the correct way of doing that, could they tell me? I know that works, but I'm sure there is a better way

it's /etc/X11/xorg.conf (case sensitive)

---

