---
title: "Switching users freezes computer"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by mole25 on 2007-05-04
When i try and switch users all i get is a black screen and nothing ever loads, and i am forced to reset the computer manually! any ideas?
thanks
mole.

---

### Post by jargoman on 2007-05-04
this happened to me when I installed the restricted drivers for my Ati graphics card. This worked like a charm for me

$ sudo gedit /etc/X11/gdm/gdm.conf-custom

a text editor will open and under where it says [daemon]

add 

AlwaysRestartServer=true

save and exit. I think you might need to reboot for the changes to take effect but it should work.

---

### Post by mole25 on 2007-05-04
cheers works great :D

---

