---
title: "MacMini PPC Dipslay resolution"
date: 2007-03-07
forum: Apple PPC Users
---

### Post by cipriota on 2007-03-07
Hi

I just installed Ubuntu 6.10 (and updates) on a MacMini PPC 1.5GHz 512MB Ram. The thing is, I can't get resolutions higher than 1024x768. My display can handle 1280x1024 max. 
After editing xorg.conf and adding "1280x1024" nothing changed.

ATI Raedon 9200 drivers seem to be installed...

Please help! 


Cheers

---

### Post by bostoys on 2007-03-08
i had the same problem, and if yours is the same as mine, go back into xorg.conf and change the default depth from 24 to 16. that's what did it for me.

---

### Post by cipriota on 2007-03-08
thanks for your help but nothing changed with 16 depth or any other depth. I noticed a message during setup "cannot allocate resource region 0 on device (...)". Does this have anything to do with my problem?

---

### Post by ssam on 2007-03-08
try running
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
in a terminal. you will be asked a few questions.

then log out

then press CTRL+ALT+backspace to restart X

then log back in.

---

### Post by cipriota on 2007-03-09
PROBLEM SOLVED. Thanks a lot ssam!!!

---

### Post by sam22 on 2007-03-09
I followed these  instructions, but when i rebooted, the screen goes black and i get a screen saying VGA mode not supported. How can i fix that. Is there any way to go back to how i had it?

---

