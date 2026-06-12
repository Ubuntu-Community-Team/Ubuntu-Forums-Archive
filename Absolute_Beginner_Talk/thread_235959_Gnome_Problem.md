---
title: "Gnome Problem"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by wespawloski on 2006-08-14
After a fresh install, everything appeared to be fine. I got past the username and password form, then nothing happened, the screen appeared blank with a maroon background. I assume that gnome did not initialise? I tried again but instead selected the failsafe session. I was presented with a "Could not find gnome installation" error. This was about the third ubuntu install of the day with the exact same problem. Any suggestions?

---

### Post by 23meg on 2006-08-14
What's your video hardware? Have you had any success with any other Linux distro?

---

### Post by wespawloski on 2006-08-14
radeon x1800xt

I've successfully installed ubuntu about 3 times before, I keep having grub problems and whatnot. With this video card, its worked before. Only just recently (I tried to install about 3 more times) my computer developed this problem. It makes me assume its something with my bios or the hard drive is dieing

---

### Post by wespawloski on 2006-08-14
no one?

---

### Post by kaamos on 2006-08-14
A failing drive sounds pretty probable to me. You can search errors on your ubuntu partition with "sudo touch /forcefsck" and reboot. Some other things to try would be to change the video driver to vesa (sudo dpkg-reconfigure xserver-xorg) or to remove the gnome conf folders (rm -rf ~/gnome* && rm -rf .gconf*)

You can get a console with ctrl+alt+f1 in the login screen.

---

### Post by wespawloski on 2006-08-14
alright, thanks. I'll give those a try

---

### Post by akniss on 2006-08-14
> **wespawloski said:**
> radeon x1800xt

I've successfully installed ubuntu about 3 times before, I keep having grub problems and whatnot. With this video card, its worked before. Only just recently (I tried to install about 3 more times) my computer developed this problem. It makes me assume its something with my bios or the hard drive is dieing

Have you been successful with this particular install CD?  perhaps you have a corrupt disc that isn't getting the job done successfully...

---

