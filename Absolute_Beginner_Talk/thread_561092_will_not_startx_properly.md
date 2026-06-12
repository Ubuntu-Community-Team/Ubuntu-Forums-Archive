---
title: "will not startx properly"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by Remix_eyeballs on 2007-09-27
when i boot my macbook, it boots ok. it gives me a terminal login, then a comand prompt.
I type in startx and it brings up the usual X shaped cursor and dotted no-wallpaper look that it always does.  

then after loading nautilus, it stops.  the computer freezes up and the only thing i can use is the cursor, which can't click.  any ideas?


edit:  I tried startxing again, and it says it can't find a number of files.

---

### Post by 5-HT on 2007-09-27
Including which files are missing in your post would be a start....
Best thing is to post a sample, only the output from one attempt, of your xorg log (from /var/log) so someone can track down the error and a solution.

---

### Post by Remix_eyeballs on 2007-09-28
the files missing are /usr/X11R6/lib/fonts/misc

/usr/share/fonts/cyrillic

/usr/X11R6/lib/fonts/Type1

I'm having trouble getting the Xorg.0.log file to copy properly.
I'll get it to you ASAP.

---

