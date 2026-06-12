---
title: "Screen problems after clean install"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Covalent Bond on 2008-01-11
Completed a clean install of Gutsy 7.10.  Currently, I have a myriad of problems that did not exist yesterday with 7.10 installed.  One problem at a time:  Because I was unable to configure Compiz, I thought the problem was NVIDIA.  Went to Administration, chose the appropriate NVIDIA driver for Ge7, choose my Dell monitor and was advised to log off.  Logged off, but now the screen does not fill the monitor at the right and left margins.  I should have left well enough alone, but ...  Other problem include no applet to configure Compiz, and VLC does not work even with the restricted drivers loaded.  For now, I will settle for the monitor issue, and work on the others later.
Thanks for any assistance.
CB

---

### Post by taurus on 2008-01-11
Try to reconfigure your X server again.

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then, <Ctrl><Alt>Backspace to restart X.

---

### Post by eapache on 2008-01-11
For your screen, it sounds like you did everything right. Now go into System>Preferences>Screen Resolution and choose the right one.

For configuring compiz, you can go into System>Preferences>Appearance and go to the last tab. It doesn't provide many options, but it will let you change things.

Taurus: it sounds like just a screen geometry problem; he has a functional display. I wouldn't have suggested reconfiguring x just yet...

---

### Post by Covalent Bond on 2008-01-11
TO:  Eapache and Tarus:  Changing the resolution resolved the issue.  Reconfiguring did not change anything.  Thanks for the help.  I will work on the other issues.
CB

---

