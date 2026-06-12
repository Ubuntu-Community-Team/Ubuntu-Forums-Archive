---
title: "out of range error"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by wwbdd on 2005-11-21
For some reasons after the cd drive was taken out and then added back in (it's a long story dont ask, it is in its original working configuration now so i dont understand where the problem came from) when i boot up the system it goes through the normal boot process and gives me the usual gdm login but then when i login the screen goes black and the monitor gives me an error out of range.  It seems this error is given by the moniter not linux sending the error to the moniter.  My guess is that somehow the screen resolution got changed (i dont know how) and now i have to go back in a fix it to resolution the moniter accepts but i dont know.  I think it's just a matter of changing a config file somewhere but i dont know what file or where it is.  Any help would be much appreciated.

---

### Post by aysiu on 2005-11-21
Press control-alt-F1.
Log in.
Then type ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Burke on 2005-11-21
I think you might be able to edit /etc/X11/xorg.conf and just remove modes that won't work.  

When your monitor gives you the error, hit Ctrl+Alt+F2.  Log in as root, then type: 

cd /etc/X11
cp xorg.conf xorg.conf_backup
nano xorg.conf

Now find the part where it lists a bunch of resolutions. Try removing some of the higher ones (ie. 1600x1200). 

Now press Ctrl+Alt+F7, then Ctrl+Alt+Bksp.  Hope for the best... you just restarted X.org.


**EDIT:** NVM, just saw aysiu's idea, and it is *much* better. :)

---

