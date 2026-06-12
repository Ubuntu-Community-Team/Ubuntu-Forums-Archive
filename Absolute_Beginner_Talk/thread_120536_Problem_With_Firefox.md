---
title: "Problem With Firefox"
date: 2006-01-22
forum: Absolute Beginner Talk
---

### Post by BugenhagenXIII on 2006-01-22
I downloaded Firefox 1.5 awhile ago, and it was working perfectly.  Until a day or two ago, that is.  Now it shuts down completely, with no error message, when some sites finish loading completely.  These forums are fine, a few of my other bookmarked sites are ok.  But when most sites finish loading, Firefox just disappears.  I have no idea whats wrong with it, and don't know how to fix it, and it's really annoying.  Any help would be greatly appreciated.

---

### Post by gsdefender on 2006-01-22
Have you tried deleting $HOME/.mozilla and re-running Firefox?

---

### Post by BugenhagenXIII on 2006-01-22
Just tried it, and the problem is still there.

---

### Post by malkaven on 2006-01-23
I had this same problem.  I was able to fix it.

I went to edit my xorg.conf

sudo nano /etc/X11/xorg.conf

Under Section "Extensions"
Option  "Composite" "Enable" 

Comment that out:
#   Option  "Composite" "Enable" 


Restart X or your computer.  Hope it works for you.

---

### Post by BugenhagenXIII on 2006-01-23
That worked, thanks.

---

