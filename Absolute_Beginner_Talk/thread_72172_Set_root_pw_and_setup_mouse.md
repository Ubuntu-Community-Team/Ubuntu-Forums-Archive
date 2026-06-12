---
title: "Set root pw and setup mouse"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by midhat on 2005-10-05
Hey how do i set the root's password. I actually need to get my serial mouse working. (its just an old three button thingy by "Genius"). So i think i will need root access to run the hardware config utility. (also tell me its name and the command to run it). I will handle the rest. 

Basiclly i installed ubuntu to setup a php development envoironment. Is that a good choice. I chose it coz its very fast as compared to other distros (but they all support my mouse:confused: )

---

### Post by Ampersand on 2005-10-05
To run a program as administrator, put 'sudo' before the command, and enter the password for your login name when prompted. In this case, 'sudo dpkg-reconfigure xserver-xorg'.

Alternatively, if you prefer, you can edit your X configuration directly using 'sudo nano /etc/X11/Xorg.conf'.

---

### Post by DJ_Max on 2005-10-05
Have you looked at:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[https://wiki.ubuntu.com/SerialMouseHowto](https://wiki.ubuntu.com/SerialMouseHowto)

---

### Post by midhat on 2005-10-06
Thank you very much ppl. Hope it solves my problem. Now please tell me if ubuntu is a good option to make my php (+mysql) development machine

---

### Post by DJ_Max on 2005-10-06
[QUOTE=midhat]Thank you very much ppl. Hope it solves my problem. Now please tell me if ubuntu is a good option to make my php (+mysql) development machine[/QUOTE]
Of course, I don't see why not. When I used PHP, Ubuntu was for development. Now I just do Ruby & Rails w/ MySQL and SQLite.

---

