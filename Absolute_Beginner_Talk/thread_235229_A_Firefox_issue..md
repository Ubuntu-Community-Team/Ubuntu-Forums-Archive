---
title: "A Firefox issue."
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by Scintillement on 2006-08-12
When I enter information into websites such as to log in a dialog box pops up telling me if the site is secure or not. There is the option to untick something and then those boxes no longer show up. My problem is I accidentilly unticked (or ticked) one that made those particular ones no longer show up.

I like those boxes. Yes I know it's odd but I do. I can't seem to find a way to get the box to come back.

I know this is poorly described, I just can't describe it better. I'm sorry. Any help or ideas is much appreciated.

---

### Post by kerry_s on 2006-08-12
preferences> advanced> certificates> ask everytime

---

### Post by pdub on 2006-08-12
Type **about:config** in the address field and hit enter

Then find the settings that begin with security.warn.

There are several options such as warn when entering a secure site

**security.warn_entering_secure**, you can set it back to true.

The items in **bold** are items that you have changed.

---

### Post by Scintillement on 2006-08-12
Is there a way to *reset* Firefox to it's *default* settings? That way I could tick or untick the boxes as they appeared for the first time again?

---

### Post by pdub on 2006-08-12
You could always create a new profile and set it as your default. This would reset firefox to default settings.

Have a look at this tweak guide for more details.

[http://www.tweakguides.com/Firefox_1.html](http://www.tweakguides.com/Firefox_1.html)

---

