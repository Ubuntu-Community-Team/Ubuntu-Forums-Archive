---
title: "OpenOffice stars without window decorations"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by ashdezign on 2008-03-15
I am using Kubuntu 7.10 and Open Office has been acting funny. It starts without window decorations and full screen for Spreadsheet, Presentation, Drawing. In OpenOffice Word Processor it starts normally, but things like Bullet menu's and Print open full screen dialogues without decoration.

In Spreadsheet, Drawing and Presentation functionality is impaired as any attempt to access menues like File, Edit, View and so on all result in the screen blinking and the menu options fail to open. I cannot save a document, print etc because of this.

I have tried uninstalling and reinstalling to no effect.

Any help would be appreciated as being unable to access office productivity software effectively cripples kubuntu for my use, and just when I was getting used to it!

---

### Post by ohzopants on 2008-03-19
I don't use KDE, but I know that there is a package that makes OpenOffice integrate nicely with gnome.  There may be a similar package for KDE, or the gnome one may be interfering (this is highly unlikely, however).  Take a look through synaptic.

Also, could you post a screenshot, or 2, since I'm not sure what you mean exactly?

---

### Post by Daveth on 2008-03-19
are you running desktop effects with compiz fusion? Just a thought. Try turning them off if you are and see if OO behaves after that.

---

### Post by ashdezign on 2008-04-06
Sorry for my delay in reply I have been offline for a bit.

Ohzopants I have attached a screenshot:


Daveth it does seem to be Compiz Fusion that is causing it, when I turn off compiz Open Office behaves fine.

---

### Post by mrboojive on 2008-04-06
Do you have the openoffice.org-kde package installed?

I'm not sure, does Compiz Config Settings Manager have a KDE equivalent? Sounds like this could be a problem with the settings in Compiz's Window Decorations plugin.

---

### Post by m4cph1sto on 2008-06-16
I'm having this same problem in gnome.  Using compiz-fusion desktop effects and emerald themes, Open Office window decorations are buggy and keep disappearing.  I'm running Ubuntu 8.04 with the most recent updates.  

Edit: On second though, this is a separate bug, probably an emerald bug.  The title bar is not being updated properly when using emerald.  By changing various button settings, I can reduce the severity of the issue.  The bug's effects are minimized by disabling "Use Button Fade" and enabling "Show Tooltips for Buttons", which seems to force the title bar to be redrawn most of the time, but not always.  

I found this bug report, which has received little attention: [https://bugs.launchpad.net/ubuntu/+source/emerald/+bug/219645](https://bugs.launchpad.net/ubuntu/+source/emerald/+bug/219645)

---

