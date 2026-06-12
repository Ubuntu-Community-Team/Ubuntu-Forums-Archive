---
title: "synaptic package manager ............help !!! Error"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by 12hello on 2007-07-09
hey when ever i start the synaptic package manager i get this error ...........................


E: Malformed line 40 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

 i was trying to download vlc payer and added repository after which i got this error ...
Please help

and if any one could help me with the steps to download vlc player could be of great help

---

### Post by AlexenderReez on 2007-07-09
so go to 

>  gksudo gedit /etc/apt/sources.list


correct line 40.....it is easier to use gedit after install gedit plugins...it has plugin to display number of line.....

---

### Post by KIAaze on 2007-07-09
What repository did you add?
VLC is in the universe repository.
If you added it through the GUI, there shouldn't be any problem.
If you added it by editing /etc/apt/sources.list, post /etc/apt/sources.list here or undo your change and add the repo through the GUI.

---

### Post by AlexenderReez on 2007-07-09
> **KIAaze said:**
> What repository did you add?
VLC is in the universe repository.
If you added it through the GUI, there shouldn't be any problem.
If you added it by editing /etc/apt/sources.list, post /etc/apt/sources.list here or undo your change and add the repo through the GUI.

undo can only possible  before you close that file...if you open it again..you won't be able to undo it...hm...ok..how about paste your source lists here?

---

