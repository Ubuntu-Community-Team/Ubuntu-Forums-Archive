---
title: "[SOLVED] Force quit the desktop..."
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by Just-trevor on 2008-04-06
I killed the desktop with the xkill function.
I did ctrl+alt+esc and then clicked on the desktop and the folders and the clicking function left.  
Everything else works, the panels, my cursor, firefox...
When I tried logging out and switching sessions to gnome and then back to Xfce the background left.  Is there a command to start it back up, or do I have to restart the computer?
(I only ask because I'll probably do it again and don't want to keep restarting)
thanks

---

### Post by Rocket2DMn on 2008-04-06
To completely restart X, do CTRL+ALT+BACKSPACE
Let me know if you have further problems.

---

### Post by Just-trevor on 2008-04-06
didn't work
I guess I'll just restart and try not to do it again.
thanks

---

### Post by Michael.Godawski on 2008-04-06
You can also try the combination 
alt + print + K

---

### Post by Rocket2DMn on 2008-04-06
I don't think you should be using the xkill function, just log out to change sessions.  Otherwise to access gnome or Xfce directly you can do something like
```
sudo /etc/init.d/gdm start|stop|restart
sudo /etc/init.d/xdm start|stop|restart
```
where start/stop/restart are your normal choices.  If you just stop them, you will probably end up at a tty, and you can start the other from there.  However, just logging out and switching sessions should be all you need to do.

---

### Post by Just-trevor on 2008-04-06
I just shut off the computer and turned it back on and it's the same

---

### Post by Rocket2DMn on 2008-04-06
When you say "the background left", what exactly do you mean?  Does the computer function normally?  Can you show me a screenshot?  Does the display look ok?

---

### Post by Just-trevor on 2008-04-06
...
the background changed to a sandy colour and I couldn't right click to change it.
I wondered what would happen if I changed the background, if it would change or not, and noticed on the Desktop Settings menu that the "Allow Xfce to control your desktop" was unchecked.  I rechecked it and everything's fine.
That was a pointless waste of time...
sorry...

at least I happened to notice that before more time was wasted... who knows how many things I might've ended up trying...
thanks

---

### Post by Rocket2DMn on 2008-04-06
Glad you got it working, not being an Xfce user, I would never have thought of that.

---

