---
title: "Changing to console mode (Xubuntu)"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Cykelbulle on 2007-04-22
I was about to configure the xorg.conf file.
Apparently I needed to have "X" closed, Im new to linux so Im not 100% sure what that means.
I searched some forums and sites for a while, and at last I found that I could press "ctrl+alt+backspace".
I tried it but I only got back to the login screen.
A friend of mine that is running Kubuntu have a option to go "Console Mode" or similar.

To not get this thread too long Ill just ask; How do I get out of this "X" and Xfce? Terminal maybe?

Regards //Cykelbulle

---

### Post by kariopto on 2007-04-22
You can edit xorg.conf and then just restart X, (ctrl+alt+backspace).
If you really want to close X, then: ctrl+alt+backspace, then ctrl+alt+F1 takes you to console mode, login and then kill gdm ```
sudo killall -9 gdm
```
If you killed gdm, you have to restart it before going back to graphics mode
```
sudo /etc/init.d/gdm restart
```
To get back to graphics mode ctrl+alt+F7.

---

### Post by Cykelbulle on 2007-04-22
Thank you, I fixed it

---

