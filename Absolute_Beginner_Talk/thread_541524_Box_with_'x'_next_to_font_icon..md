---
title: "Box with 'x' next to font icon."
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by OziD on 2007-09-02
Hey guys I am pretty new to ubuntu. I've been messing with it for a few months, and am learning a lot thanks to the forums. I installed some fonts (by moving the fonts to 'fonts:///')

They are TTF fonts. Most of them work, except for a few. Lucida Grande is one of them. 

When I navigate to the location of the fonts, it shows the font Icon with it displaying properly, except there's an X in the corner. When I try and use the font, it shows up at boxes, no matter what character is used.

Any ideas on what I did wrong? Some of the fonts I installed this way work.

Here are some screenshots of what I am talking about.

---

### Post by jordanmthomas on 2007-09-02
Here's how I install fonts and it works flawlessly (even with Lucida Grande, I might add)

1.  Make a folder in your home directory and call it .fonts  (note the .)
2.  put fonts there.
3.  Any time you add new fonts, run
```
sudo fc-cache -f
```
4.  You're good to go.

Before you do this, run
```
gksudo nautilus
```
go to fonts:/// and remove the offending fonts.

Hope this helps.

**PS  the x on the icon for the font probably means the file isn't readable (because of permissions) for some reason

---

### Post by OziD on 2007-09-04
Thanks. trying right now. :)

---

