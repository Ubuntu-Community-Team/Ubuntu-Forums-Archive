---
title: "wine problems"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by pdlethbridge on 2007-08-18
After installing wine, I can't find its icon any where. There are some files missing and i can't get them to load in synaptic. TIA

---

### Post by Kosimo on 2007-08-18
Wine doesn't really have an icon.
Try to open a terminal and write this:

> wine --version

If it says the version you have it means is installed.
Every time you want to open some *.exe file with wine I recommend to do it in the terminal by going to the folder you have the file and then wine (file).exe 
Wine itself it creates a folder (where you can find the installed programs) in home directory. If you want to see it from nautilus press (CONTROL + H) and you'll see the hidden directoreies have a look to .wine

Here some useful wine commands:

wine uninstaller (to uninstall some windows apps) 
winecfg  (a kind of mini control panel of wine)
wine --version (the current version installed in your system)

Hope this information is helpful.

From Catalonia.

---

### Post by pdlethbridge on 2007-08-18
the package I seem to be missing is something like lowvoice.nl. I have had an icon in past installs but not this one?????????/I'm using ultimate ubuntu

---

### Post by aysiu on 2007-08-27
Wine doesn't have an icon.

Here's a tutorial on how to use Wine:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

