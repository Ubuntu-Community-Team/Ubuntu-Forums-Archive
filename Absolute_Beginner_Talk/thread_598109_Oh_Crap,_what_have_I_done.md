---
title: "Oh Crap, what have I done??"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by ravi_s on 2007-10-31
OK, I did something really stupid.
I'm desperate to get the touchscreen working on my tablet pc so I read somewhere that all you had to do is to remove the hash from a few lines in the xorg.conf file that commented out the Wacom tablet. I did this but like a total tool, I removed the hash from the comment line that said something like 'Remove hash for Tablet' or something insted of just removing it from the 4 lines of code underneath.
When I restarted, all my graphics were reset to 800 X 600 and my graphics card is set to VESA. I've tried to change the settings but it doesn't keep the card settings whatever I do , 

I tried to re-edit the xorg.conf file and all the lines I edited have all vanished and the whole file looks different.

Have I broken something?

I'm desparate no to re-install again - I've done that 3 times already.

Please help, I dont know what to do.

R.

---

### Post by BrendanM on 2007-10-31
```
sudo dpkg -reconfigure xserver-xorg
```

Learn it, use it, love it.

---

### Post by CaptainInsaneO on 2007-10-31
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Learn this too.

Have you tried navigating to the /etc/X11 directory to see if there are any auto-backups in there that you can restore?

A word of wisdom for you, since I do networking for a living I keep a thumb drive in my pocket at all times with things like Exchange, the Admin Pak for windows, and ERD commander on it. I ALSO keep my xorg.conf on there, as well as various other backups in other locations. I learned that the hard way. One of the most important things for me (since I'm a video and graphics FREAK) is my xorg.conf.

---

### Post by ravi_s on 2007-10-31
Phew,
There were backups so I just copied from the good one to the nasty one and it all worked!
Thx CaptainInsane, you saved the day!

R.
ps the Wacom thing didn't work anyway :(

---

### Post by CaptainInsaneO on 2007-10-31
Glad to hear we got you all fixed!

Just out of curiosity, who manufactures your tablet pc?

---

