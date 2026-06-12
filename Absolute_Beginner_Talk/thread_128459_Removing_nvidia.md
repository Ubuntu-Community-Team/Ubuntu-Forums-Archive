---
title: "Removing nvidia"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by DannyX0 on 2006-02-11
I'm trying to follow these directions for instaling xgl on kde
how can I uninstall:
nvidia-glx and nvidia-kernel-common
I'ma complete n00b at this stuff please help?
Thanks alot

---

### Post by taurus on 2006-02-11
sudo apt-get remove nvidia-glx nvidia-kernel-common

or 

man apt-get

for more info...

---

### Post by DannyX0 on 2006-02-11
Thanks alot!

---

### Post by DannyX0 on 2006-02-11
It asks for a password and then it says:
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Then I type that in and it says
> dpkg: requested operation requires superuser privilege
how do I fix that?

---

### Post by taurus on 2006-02-11
I assume you are logged in to Gnome and X uses nvidia driver.  You probably need to modify your /etc/X11/xorg.conf and change the line from "nvidia" back to "nv" first.  Then restart X (or reboot if you don't know how to restart X) and see if you now can remove nvidia driver...

---

