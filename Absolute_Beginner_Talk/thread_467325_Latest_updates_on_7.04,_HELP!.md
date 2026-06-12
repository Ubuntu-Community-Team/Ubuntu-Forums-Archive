---
title: "Latest updates on 7.04, HELP!"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by MikeJ112 on 2007-06-07
Have just reformatted the hard-drive and installed a fresh ubuntu 7.04, booted up fine! I installed the 50 updates, rebooted, and now when I sign in I just get the mouse pointer and my wallpaper. Whats happened??

---

### Post by MikeJ112 on 2007-06-07
Has anyone else had this problem?

---

### Post by ICUR2Ys on 2007-06-07
Not exactly the same problem but I had a bad load of the kernal and had to reinstall.  I installed the apprx 7 files relating to the kernal first by themselves then reboot to be sure it is ok then installed the rest of the updates.

---

### Post by MikeJ112 on 2007-06-07
Is it fixable then or would I need to reformat and reinstall?

---

### Post by w4ett on 2007-06-07
Can you load the prior Kernel .15?

---

### Post by sailor2001 on 2007-06-07
you could try:  sudo killall gnome-panel     and then :     gnome-panel

---

### Post by MikeJ112 on 2007-06-07
Yup, booted up ok on .15

---

### Post by w4ett on 2007-06-07
Go to Synaptic Package Manager and search for linux-image. select the newer kernel, delete it, then reinstall.   See if that works.

---

### Post by carlo bolzonello on 2007-08-03
i have a similar problem, however i get only a black csreen with the cursor only, my machine just hangs. i have tried to run 1.5, using the commands "you could try: sudo killall gnome-panel and then : gnome-panel " however nothing. i think i need to re-install.

---

