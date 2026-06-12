---
title: "Remove Gnome (original) Panels"
date: 2010-12-31
forum: Art &amp; Design
---

### Post by Jackxn on 2010-12-31
Hi!

I just installed the Avant Window Navigator which works fine and contains all the functions i need on this PC.

Now i would like to remove the built-in Panels but i cant remove the last of them, no matter which one i start with, the last one cant be removed by right-clicking --> delete panel.

I tried removing the gnome-panel package (along with some others that were linked to it) but it seems that this only led me to reinstalling Ubuntu, because it kind of crashed right after logging in and getting me back to enter my password again and again without showing the desktop.

There was some short error message that disappeared too fast to be able to decipher it.

Can anyone help me with this?
Is it possible that the compiz package caused the crash instead of the missing gnome-panel package?

---

### Post by Elfy on 2010-12-31
[http://ubuntuforums.org/showthread.php?t=1444461](http://ubuntuforums.org/showthread.php?t=1444461)

That should help you out.

---

### Post by howefield on 2010-12-31
Have a look at this thread.

[http://ubuntuforums.org/showthread.php?t=1444461&page=1](http://ubuntuforums.org/showthread.php?t=1444461&page=1)

Edit: Too slow ;-)

---

### Post by Kalimol on 2010-12-31
One thing not noted in that thread is that after you change the gconf key, you'll want to install xfce-utils or whatever it's called and bind Alt+F2 to the command xfrun4. This is because Alt+F2 in Gnome isn't a command - it's a dialog spawned by the Panel application. You can't have the one without the other.

Xfrun4 is not quite as nice as Gnome-Panel's Alt+F2, but it still performs the same basic function of being good for launching things in an emergency; it doesn't give you a searchable list, but it will remember and autocomplete any command you input. Gnome Menu will pick up the switch, too, so that you get the same Run dialog (the XFCE one) when you select Launch from Avant's Gnome Menu.

(Now if only Avant had a backlight control applet. The one thing I'm still missing. Blech.)

---

