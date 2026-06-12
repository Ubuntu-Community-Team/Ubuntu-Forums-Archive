---
title: "My Appearance manager is glitchy"
date: 2007-12-15
forum: Art &amp; Design
---

### Post by arvvvs on 2007-12-15
Well whenever I load Appearance manager in Ubuntu, and I want to install a new theme, I click the install button, and then the window manager that comes up is well, not exactly comming, its like its loading but it isn't.
PS I running gutsy.

---

### Post by SunnyRabbiera on 2007-12-15
hmm, well are you using themes from gnome look?

---

### Post by smartboyathome on 2007-12-15
> **arvvvs said:**
> Well whenever I load Appearance manager in Ubuntu, and I want to install a new theme, I click the install button, and then the window manager that comes up is well, not exactly comming, its like its loading but it isn't.
PS I running gutsy.

Could you post a screenshot of it? It sounds suspiciously like compiz screwing with you.

---

### Post by Juffo-Wup on 2007-12-15
Does the window that comes up  look mostly blank and becomes unresponsive?

I had a similar problem with the Appearance dialog, and it was caused by [a bug in the gtk-qt-engine]("http://https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/154871"). Removing said package got rid of the problem.

---

### Post by arvvvs on 2007-12-15
Ok it is blank and uresponsive and i use gnome look

---

### Post by smartboyathome on 2007-12-15
Do you have the plugin installed as stated above?

---

### Post by arvvvs on 2007-12-15
I have compiz yes i had same prob as the bug report.  I'm looking at it
How do i unistall it?

---

### Post by smartboyathome on 2007-12-15
Try running this:

sudo apt-get remove --purge gtk-qt-pixmaps

Then restart and see if it helps.

---

### Post by arvvvs on 2007-12-15
Working fine now, I just went to synapatic and removed it :)

---

