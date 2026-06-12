---
title: "Command line editor needed."
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by stroopwafel on 2007-01-04
I'm using Xubuntu.

I changed etc/X11/xorg.conf and now my xserver doesn't start.

What editor should I use from the command line to change the file to the original state. (I have copied the part that I deleted and saved it under a different file name, but I haven't made a copy of the whole original file... aaargh.)

---

### Post by bastiegast on 2007-01-04
there are plenty, try nano, its quite easy and straightforward. Installed by default afaik, if not: ```
sudo apt-get install nano
```
You can also try vi, which is slightly more complicated if you don't know how it works.

Good luck on fixing your xorg.conf.

ps. sudo vi /etc/X11/xorg.conf are probably the most typed word combination on my keyboard when I used to break X servers :p

---

### Post by meng on 2007-01-04
nano
vim

e.g.
sudo nano /etc/X11/xorg.conf
(nano is easier than vim if you're a novice to console editing)

---

### Post by stroopwafel on 2007-01-04
Thanks guys,

nano did the trick. I was sweating for a while... but I'm breathing again. Xserver started again.

---

### Post by meng on 2007-01-04
The "safer" way to change the xorg settings is this:
sudo dpkg-reconfigure xserver-xorg

---

