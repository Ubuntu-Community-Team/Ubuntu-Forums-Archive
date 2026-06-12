---
title: "gnome-app-install issues"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by tbonepower07 on 2007-03-14
I am very new to ubuntu and have only had it several days, and feel like I'm getting the hang of it (its wonderful).  However, I have a small problem thats cropped up, and I have no idea why.  The Add/Remove Applications utility (the gnome-app-install package) loads correctly, but after the progress bar "checking installed/avaliable applications" bar completes, the utility disappears.  It does not seem to crash, because everything else seems normal, and no crash report is generated.  Its also not running in the background; I can watch the process gnome-app-install appear on and then disappear from the System Monitor.  I also have the same problem with Automatix2, also an installer, so I feel the problem might involve some conflict.  I have no problems with Synaptic Package Manager or, correct me if I'm wrong, the gDebi package installer.

I uninstalled and reinstalled the gnome-app-install package, as well as app-install-data.

What steps should I take to correct this?

-- Jack

---

### Post by tbonepower07 on 2007-03-14
Or, is there a good alternative to the gnome application manager that I can use?

---

### Post by Monster_user on 2007-03-19
It seems to be a python2.5 issue, that only affects some systems.

frank_castle reported that using Python2.4 solved the problem.
[quote=Monster_user]Actions -> Run -> gksu nautilus

Then browse to "/usr/bin/". It may take a few minutes to load, so be patient.

Then click on any file, and quickly type "pyt", or find the "python" file. Right-click it, and select "Properties". You should be able to change the target of the link to "/usr/bin/python2.4".[/quote]

---

