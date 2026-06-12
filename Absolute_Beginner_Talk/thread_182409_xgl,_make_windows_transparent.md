---
title: "xgl, make windows transparent"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by joshrobinson on 2006-05-26
how do i make my standard everyday windows semi transparent, say my buddy list, my file browsers etc.  i know u can make the title bar transparent, and when you move windows.. but how about just normal

---

### Post by bluevoodoo1 on 2006-05-26
should be alt+ mouse wheel up/down (if I understand you correctly).

---

### Post by jasay on 2006-05-26
If you are using a new version of compiz try using the state plugin.  In gconf-editor navigate to /apps/compiz/plugins/state/screen0/options and putting something like p:gaim:70 into the opacity key on the right (where gaim is the program name as you would run it in the terminal and 70 is the desired transparency).  

You can also try holding alt and using the scrollwheel to play with transparency, but it does not reapply if you close/reopen the program.

---

### Post by joshrobinson on 2006-05-26
[QUOTE=jasay]If you are using a new version of compiz try using the state plugin.  In gconf-editor navigate to /apps/compiz/plugins/state/screen0/options and putting something like p:gaim:70 into the opacity key on the right (where gaim is the program name as you would run it in the terminal and 70 is the desired transparency).  

You can also try holding alt and using the scrollwheel to play with transparency, but it does not reapply if you close/reopen the program.[/QUOTE]

ahh thanks.. before the mouse wheel wasnt working, i forgot i switched from the vanilla package to the standard compiz package earlier and havent tried since.. the vanilla didnt have the state package either, so thats good to know :-D

---

### Post by Jeremiah478 on 2006-08-14
I got this working for most programs, but I was wondering if anyone knew how to get this working for konsole.

---

### Post by Hex0x75 on 2006-08-14
Alternatively you can also use the transset application. First you will need to install the application by typing:

sudo apt-get install transset

After it installs, create 2 launchers on your desktop, one to make transparent and the other to make non-transparent. For the transparent launcher name it whatever you want so that you know what it is, and for the command just type in 'transset'. For the other launcher, to be non-transparent, for the command type in 'transset 1'.

Now, whenever you want a window transparent, just launch the transparent launcher and your cursor will change to a cross-hair cursor, now click the window that you want to be transparent, and it will be. 
To make a window non-transparent, launch the non-transparent launcher and again the cursor will change, and just click the window that you don't want to be transparent anymore.

This is what I had to do with the vanilla package. It works just fine. Too bad I couldn't get the ALT-mousewheel to work in the vanilla.

Hope it helps.
Hex0x75

---

