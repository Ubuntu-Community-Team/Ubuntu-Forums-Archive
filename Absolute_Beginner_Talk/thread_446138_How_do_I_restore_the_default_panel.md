---
title: "How do I restore the default panel"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by BobLand on 2007-05-16
I've been adding icons to the panel.  Over time it the entire screen began to blink when some commands were issued.  I created a new user with no embellishments other then root privileges.  This user does not blink for anything.  I'm not sure if it's panel related or something else.  

I added ReminderFox to FF, Lightning and calendar_sidebar to TB2 but removed both (not ReminderFox).  I've update codecs. 

My concern is the blink is happening more often in different ways.

Thanks,
bobland

---

### Post by steve.horsley on 2007-05-16
Try logging out, changing to a terminal with Ctrl-Alt-F1 and logging in on the console. Then rename these 5 directories like this:
[B]mv .gconf .gconf-old
mv .gconf2 .gconf2-old
mv .gnome .gnome-old
mv .gnome2 .gnome2-old
mv .gnome2_private .gnome2_private-old[/B]

The Ctrl-Alt-F7 back to the GUI and log in. 
If that doesn't fix it, log out again, back to the console, delete the new directories it made and rename the old ones back again, and back to the drawing board.

---

### Post by powder on 2007-05-16
All that's really necessary is
```
rm -rf ~/.gconf/apps/panel
```
Then CTRL+ALT+BACKSPACE

---

### Post by steve.horsley on 2007-05-16
Excellent.
I've never really been sure what they hide in each. Or why they need so many different folders.

---

### Post by BobLand on 2007-05-16
I ran this code:
rm -rf ~/.gconf/apps/panel

Didn't do anything  at all.  Logged out, logged in.  Restarted.  Nothing.

Ran Steve's suggestion.  Right on the money.

Thanks to all,
bobland

---

### Post by ntu on 2007-11-07
> **powder said:**
> All that's really necessary is
```
rm -rf ~/.gconf/apps/panel
```
Then CTRL+ALT+BACKSPACE

This worked for me. Thank you Powder.

---

### Post by jfank on 2007-11-14
I tried to do that myself, and I put in the code and instead of hitting enter I did the CTRL-ALT-BACKSPACE, and it didn't do anything.  My entire panel got deleted somehow, and I'm trying to get it back to the original panel look as it was when I installed Kubuntu on my computer.  I don't get the mini icons or anything on the panel.  Can someone help me with this one?  I'm trying to keep from re-installing Kubuntu on my computer.  Thank you.

---

