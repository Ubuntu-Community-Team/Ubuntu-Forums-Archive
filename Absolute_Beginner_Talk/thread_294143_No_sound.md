---
title: "No sound"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by caseymoore on 2006-11-06
Please help!
Xine crashed whilst playing a DVD. Now I have no sound. I've rebooted twice but I still have no sound

---

### Post by tc10b on 2006-11-06
try this script, it used to work for me under breezy

sudo /etc/init.d/alsa force-reload

it should reload the sound device for you.

---

### Post by caseymoore on 2006-11-06
When I put it in the terminal I got this:

casey@Computer:~$ sudo /etc/init.d/alsa force-reload
Password:
sudo: /etc/init.d/alsa: command not found

---

