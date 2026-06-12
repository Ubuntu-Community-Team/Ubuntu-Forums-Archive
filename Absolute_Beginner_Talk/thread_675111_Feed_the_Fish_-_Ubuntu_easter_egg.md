---
title: "Feed the Fish - Ubuntu easter egg"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by aBitLater on 2008-01-22
I was at an easter egg website and it mentioned that Ubuntu has an easter egg in it.

I'll leave it up to others to search if they're interested in finding it out, but I'm only curious to know how to "kill" the fish after feeding it?  It was cute and funny to see, but now do I have to reboot?

Thanks in advance!

---

### Post by jan quark on 2008-01-22
You’ll have to run this command to disable the fish, which will restart your gnome panels, but not your applications.

killall gnome-panel

---

### Post by seventhc on 2008-01-22
you can just <Ctrl-Alt-Backspace> then log back in, but there is no way of ending that fish while remaining logged in. AFIK.

---

### Post by aBitLater on 2008-01-22
so, after <Ctrl-Alt-Backspace>, I assume I'll be at a terminal prompt.

Do I "startx" at that point, from the terminal?

TIA

---

### Post by koleoptero on 2008-01-22
> **aBitLater said:**
> so, after <Ctrl-Alt-Backspace>, I assume I'll be at a terminal prompt.

Do I "startx" at that point, from the terminal?

TIA

Ctrl-Alt-Backspace restarts X, it does not simply kill it, so you'll be back at the usual login screen immediately.

---

### Post by The Cog on 2008-01-22
Alt-Ctrl-Backspace drops you toa terminal for a few seconds, but X restarts. 
jan quark is right though, 
**killall gnome-panel**
in a terminal window will get rid of the fish.

---

### Post by Steveway on 2008-01-22
Also the fish is called Wanda.
Just in case anyone wants to know her name.

---

