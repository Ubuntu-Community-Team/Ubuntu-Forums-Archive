---
title: "Help me install fonts, please!"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by bean77 on 2007-06-04
I don't understand this:  (from [www.dafont.com](www.dafont.com))

> 
**How to install a font under Linux ?**

Copy the font files (.ttf or .otf) to fonts:/// in the File manager.

File manager?  Am I looking in the wrong place?

---

### Post by nerdpony on 2007-06-04
Actually, I was just about to post a *really* similar question- I'm currently dual-booting XP and Ubuntu and want to find out how to make all of my fonts accessible through Ubuntu.  Anyone know?

---

### Post by starcraft.man on 2007-06-04
[I think this is what your looking for. ]("http://penguinfonts.com/howto/ubuntu.php")Just did a search and it explains it well enough. Try whichever way you prefer.

---

### Post by trak87 on 2007-06-04
There's probably a tutorial somewhere, but here's what I do:

```
sudo mkdirhier /usr/share/fonts/truetype/myttfonts
sudo cp *ttf /usr/share/fonts/truetype/myttfonts
sudo chown root: /usr/share/fonts/truetype/myttfonts/*
sudo chmod 644 /usr/share/fonts/truetype/myttfonts/*
sudo fc-cache /usr/share/fonts
```

The first line creates a directory in the system font area for your new fonts. The second line copies your ttf files into that directory. Third line makes sure root owns the fonts. Fourth line gives the fonts the correct permissions. The last line builds the font info cache.

Now, restart the font viewer (or Firefox or any other app that uses fonts) and you should see the new fonts available.

---

### Post by bean77 on 2007-06-04
> **starcraft.man said:**
> [I think this is what your looking for. ]("http://penguinfonts.com/howto/ubuntu.php")Just did a search and it explains it well enough. Try whichever way you prefer.

Thank you!

---

