---
title: "Need help with my moniter and ubuntu"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by wahoo on 2006-08-06
ok so a while back I installed ubuntu and it was all fine, Then i purchased a Viewsonic VA1912wb Widescreen moniter.

So i turn on my computer with my new moniter all fresh n' clean, and all is fine, Then I get to the login screen and it wont show up. my moniter says "out of range," And has 2 things like a:

v:and a number
h:and a number

Whats the deal, will my moniter not work with ubuntu?

TIA for any help.

---

### Post by kebes on 2006-08-06
Hmm... If you are comfortable with the command-line, this is what I would recommend:

1. Go to a terminal prompt (Ctrl+Alt+F1 (or F5 or whatever) to get to a free terminal). Hopefully this will show up on screen since it is in a very basic VGA mode.

2. Modify "/etc/X11/xorg.conf":
$ sudo nano /etc/X11/xorg.conf

3. Find the current screen settings and change the horizontal and vertical syncs to match what you need. Check the manual for your monitor to find the right range. Be warned that some equipment can be damaged if supplied with a sync well outside of the expected range. You may need to do a bit of searching for "xorg.conf" configuration options, so that you know how to specify "H" and "V".

4. Return to your GUI session (Ctrl+Alt+F7) and restart it (Ctrl+Alt+Backspace). Or just restart your computer and see if the screen now works. You might also consider going into a "non-optimal" graphics mode (something simple like 800x600) just so you can get into Ubuntu and then change teh graphics mode with the GUI tools until it is right.


If you are not comfortable with the command-line, then I would go back to your old monitor momentarily, so that you can get back into your Ubuntu GUI. Then change the video settings to something simple (800x600 with a vertical and horizontal sync in the range that your new monitor requires), then switch to the new monitor (and do Ctrl+Alt+Backspace if you have to). Hopefully you will then see everything on screen (at low resolution) and you can tweak the settings until everything looks right.

Hope that helps.

---

### Post by Phasmagon on 2006-08-06
I would recommend:
Alt+F1
type in the terminal:*sudo dpkg-reconfigure xserver-xorg*
then Alt+F7
then Alt+Ctrl+Del

---

### Post by wahoo on 2006-08-06
im trying those out, i tryed the first one but it was too confusing so im trying the second.

---

### Post by blicksky on 2006-08-06
I am having a very similar problem with my ViewSonic VA712b LCD monitor.  Whenever I set Gnome's resolution to 1280x1024 (the LCD's native resolution), the LCD displays a message saying "out of range".  Only if I set Gnome's resolution to 1024x768 will it display properly.  I've tried all sorts of changes to xorg.conf, including setting a modeline and running the reconfigure script.  Any advice would be appreciated.

---

