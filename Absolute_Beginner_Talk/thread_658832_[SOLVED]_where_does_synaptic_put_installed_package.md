---
title: "[SOLVED] where does synaptic put installed packages?"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by derkaderka on 2008-01-05
whenever i install something using the synaptic package manager, i never know where it goes.  there arent any new icons, and no new menu options.  the only solution i have found is to dig through the logs and find where it put the specific files (usually ends up in /usr/<something>), then go there directly looking for an .exe file.  this usually doesnt work, however, and i get a whole variety of errors.

how do i get synaptic to put newly installed programs somewhere logical (like its own folder under /home), and then put a link to the .exe on the desktop?

---

### Post by Xavieran on 2008-01-05
Linux doesn't use .exe files...
Linux puts the installed files' launchers in /usr/bin (usually) you can run these from a terminal with ```
yourapp
```

To make a launcher for one simply right-click on the desktop select create launcher ...fill in the options given...

---

### Post by ugm6hr on 2008-01-05
What programs are you talking about?  And are you using the standard Ubuntu (Gnome)?  If so, Gnome should auto-update the menu to include the installed program.  It certainly does on mine.

---

### Post by rubicon on 2008-01-05
> **derkaderka said:**
> whenever i install something using the synaptic package manager, i never know where it goes.  there arent any new icons, and no new menu options.  the only solution i have found is to dig through the logs and find where it put the specific files (usually ends up in /usr/<something>), then go there directly looking for an .exe file.  this usually doesnt work, however, and i get a whole variety of errors.

how do i get synaptic to put newly installed programs somewhere logical (like its own folder under /home), and then put a link to the .exe on the desktop?
One word: FHS. [Filesystem Hierarchy Standard.](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

Thus installing apps into your /home/user folder isn't good. Synaptic doesn't allow user to pick destination for files. Fortunately :) Otherwise, novice users will experience HUGE problems with modules dependencies and linking all parts of program/library into one working piece, That's briefly said.

If you wondering where are newly installed files are, look into 'Synaptic, properties of package > Installed Files' or use command-line utilities like 'whereis', 'which', 'locate' and 'find'.

---

### Post by derkaderka on 2008-01-05
> **Xavieran said:**
> Linux doesn't use .exe files...
Linux puts the installed files' launchers in /usr/bin (usually) you can run these from a terminal with ```
yourapp
```

To make a launcher for one simply right-click on the desktop select create launcher ...fill in the options given...

precisely the answer i was looking for, thank you

---

