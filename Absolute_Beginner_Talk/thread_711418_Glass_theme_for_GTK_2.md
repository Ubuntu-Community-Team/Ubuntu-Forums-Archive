---
title: "Glass theme for GTK 2?"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-02-29
I would like to have a nice, simple, clean glass border theme. Or even a glass human theme!! 
I have an intel 965 X3100 chipset :( its been blacklisted. (I have taken it off the blacklist but put it back on as for oblivious reasons). 

Is there a theme out there which will work or do I need compiz to be on? 

********Do not want Vista themes/glass/boarders.. I just came from vista. Want something new and fresh.*******

Thanks!!!

:KS

---

### Post by Tom--d on 2008-02-29
I would like to have a nice, simple, clean glass border theme. Or even a glass human theme!! 
I have an intel 965 X3100 chipset :( its been blacklisted. (I have taken it off the blacklist but put it back on as for oblivious reasons). 

Is there a theme out there which will work or do I need compiz to be on? 

********Do not want Vista themes/glass/boarders.. I just came from vista. Want something new and fresh.*******

Thanks!!!

:KS

---

### Post by Tom--d on 2008-02-29
How do I get this theme working? 

[Here]("http://mariuxv.deviantart.com/art/Aureus-Mariux-Theme-78193699")

I need the emerald bit, but I cant extract it? Help?

---

### Post by SunnyRabbiera on 2008-02-29
you can get emerald in the repositories, go to system> administration> synaptic package manager
once it is loaded search for emerald.

---

### Post by Hospadar on 2008-02-29
if you want transparency, you are going to need compiz (I believe).  Have you tried installing the restricted drivers for your card through the restricted drivers manager?  System->Administration->Restricted Drivers Manager

Emerald is a window decorator that requires a composter like compiz (again, not sure, but pretty sure).  If and when you get compiz working then you can install emerald, do Alt-F2 ```
emerald --replace
``` to start it up.  you may want to grab the " "emerald-themes" package to get a nice set of default themes.  I'm not sure it's in the gutsy repos, you may have to download the deb manually from feisty [here]("http://packages.ubuntu.com/feisty/all/emerald-themes/download").  After you get emerald up, you can add themes in their manager System->Preferences->Emerald Theme Manager.

---

### Post by Tom--d on 2008-02-29
I've got emerald now. 

I've imported the file in Emerald Theme Manager.. What do I do next? Nothing has changed

---

### Post by Tom--d on 2008-02-29
I have the graphic drivers, its just my graphic card has been blacklisted because of bugs.

I can take it off the blacklist and get compiz working is jsut then vlc player will not work.

---

### Post by Therion on 2008-02-29
Maybe you'd like [Coal and Glass](http://www.gnome-look.org/content/show.php/Coal-and-Glass?content=74994)?

---

### Post by owbizi on 2008-02-29
Well, you have a similar problem that he has: [http://ubuntuforums.org/showthread.php?t=711334](http://ubuntuforums.org/showthread.php?t=711334).

Basically, compiz and vlc do not "stand" together, so, when you use one, you have to disable another. Or I think so... anyway, to do this more easily, install libgnome-compiz-manager0 via apt-get. Then you can enable/disable compiz with one click on the icon at the notification area.

edit: hmm, I think I misunderstanded what you said, sorry. However, a GTK theme is included on that theme, isn't it?

---

