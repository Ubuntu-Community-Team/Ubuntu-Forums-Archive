---
title: "2 annoying issues"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-01-29
Greetings all:

ok, i need to do a reconfigure xserver.xorg i think cause i get a black background then it loads to my screensaver..(just takes forever for the mouse to move across the screen)

Could it be I accidently have the X window manager and must get rid of it? how would i do this without fouling up all my settings...etc

---

### Post by sports fan Matt on 2008-01-29
the other one i thnk i can figure out, the ddesktop failed to start the gnome background, but everything came up fine..any suggestions?

---

### Post by Amstell on 2008-01-29
make a backup or your xorg.conf

cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

then if anything ***** up just do

cp /etc/X11/xord.cong-backup /etc/X11/xorg.conf

cheers

---

### Post by sports fan Matt on 2008-01-29
cp: cannot create regular file `/etc/X11/xorg.conf-backup': Permission denied
I wonder why?

---

### Post by Amstell on 2008-01-29
sorry but 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

you need to have admin access.

---

### Post by sports fan Matt on 2008-01-29
I guess im confused..I will list the symptoms of my computer and see if it helps..

1.  The computer boors up, but it seems like when it boots i get a black screen and it tajkes a long time for a response from the mouse and such (drags)

2.  I have alot of X things in my programs like things from x11..etc that i dont remember installing..I think i installed most of the x window enviroment but im not sure..

Sorry i feel like a moron, but at least im learning, arent i?

---

