---
title: "Changing Default Cursors?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by dylan623 on 2007-06-18
I'm having trouble with default cursors. I never could figure out how to change them, and when I installed the Chameleon theme it became the default. I have no idea how change it back and I would like Human to be the default again.

---

### Post by swoll1980 on 2007-06-18
I'v been wondering this myself

---

### Post by allix on 2007-06-18
System -> Preferences -> Mouse?

---

### Post by rickycodie on 2007-06-18
here you go

[http://ubuntuforums.org/archive/index.php/t-8557.html](http://ubuntuforums.org/archive/index.php/t-8557.html)

---

### Post by linuxwizard on 2007-06-18
Install gcursor once installed should show all cursor themes that you have installed can change cursor themes anytime you want


Changing Mouse Cursor Themes

Ubuntu 6.06 and 7.04:

    *

      Download the theme to an easily accessible location; ~/Desktop is good.
    *

      Install the gcursor package via Synaptic Package Manager or apt-get.
    *

      Start gcursor with System &#8594; Preferences &#8594; Cursor Selection.
    *

      Select a theme, or click 'Install theme' and select the compressed file to add it.
    *

      Once you're finished, select the theme you want to use and click "Close"

---

### Post by dylan623 on 2007-06-18
I already saw that page, it doesn't help.

---

### Post by loseyou2him on 2007-06-22
I think what is being asked here, and what I'd like to know as well, is how to change the cursor not just in gnome, but change it for xorg.  In other words a system wide change.  For those of us to use fluxbox and the like, changing the cursor this way is the best option.

---

### Post by moore.bryan on 2007-06-22
[I]best way i've found is to download the cursor theme and extract into your ~/.icons folder.  if you don't have one, make it.  then edit your ~/.Xdefaults file to include a line which reads
```
Xcursor*theme:the_name_of_your_theme
```
restart x and presto, system-wide reconfig.
[/I]

---

### Post by DonnieP on 2007-06-22
sudo update-alternatives --all
This will prompt you through every X system default there is if you have other defaults besides just the cursor you wish you could change.

sudo update-alternatives --config x-cursor-theme
This will prompt you to change the X system cursor default only.

---

