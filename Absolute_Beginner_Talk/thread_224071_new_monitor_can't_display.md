---
title: "new monitor can't display"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by Aximilli on 2006-07-27
So today I moved my ubuntu server to another workstation with a flat-panel monitor hooked up to a K.V.M.. Now once it gets past the Ubuntu loading screen, my monitor tells me it can't display the video mode. It's obvious I need to reset my xorg settings, but I have no clue how to do it blind. Or at all. What to do, oh what to do?

---

### Post by rck_hitokiri on 2006-07-27
try this stuff..... i hope it helps.....
To edit from within gnome run:

gksudo gedit /etc/X11/xorg.conf

To edit from a command line use:

sudo nano /etc/X11/xorg.conf

To configure Automatically run:
sudo dpkg-reconfigure xserver-xorg ( here you can do it automatically. )

hope this little thing helps. im a newbie to :)

---

### Post by Aximilli on 2006-07-27
Well what I need before I can even do this is the hot-key command to drop down to a text based system. Then I can try those commands

---

### Post by avtolle on 2006-07-27
CTRL/ALT/F1(or F2...F6)

---

### Post by Aximilli on 2006-07-27
Thanks guys. That did the trick (with the help of a co-worker who knew how to kill the running xserver) and I'm back on.

---

