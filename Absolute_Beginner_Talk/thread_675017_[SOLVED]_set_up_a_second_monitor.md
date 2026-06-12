---
title: "[SOLVED] set up a second monitor"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Jeezus on 2008-01-22
I have a toshiba Satellite A105 laptop, and under windows, I was able to switch the video output to another monitor plugged into my laptop. How would I do this in Gutsy Gibbon?

---

### Post by Ocxic on 2008-01-22
if you have an Nvidia video card then you can use nvidia-settings.
otherwise you could try the screen and graphics preferences in the system->admin menu
or you could try editing the /etc/X11/xorg.conf file manually, 

NOTE: Before doing anything backup or make a copy of /etcX11/xorg.conf to make sure you can always go back to your current configuration if anything goes wrong.

---

### Post by Jeezus on 2008-01-22
Thanks!

---

### Post by Jeezus on 2008-01-22
I don't know why I don't see some of these incredibly obvious things sometimes... =p

---

