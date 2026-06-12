---
title: "Hp Dj 3520 Problem"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by Shin_Gouki2501 on 2007-09-28
Hello i have also a HP DJ 3520 but its not printing at all!
Im running Xubuntu 7.04.
i used this ppd file:
[http://www.openprinting.org/show_pri...P-DeskJet_3520](http://www.openprinting.org/show_pri...P-DeskJet_3520)

from there to install the driver with cups, but it didnt seem to work? :/
When try to print Test page it pulls in the paper the print head is movin , but the paper stays clean.
tried Printing in FireFox also  uses paper but just white paper cames out...
The printer works with widnows so the hardware IS ok!

Do u have suggestion how i can verify that my printer is correctly is installed ( without printing?) in CUPS?

U have some ideas for me? 
im quite helpless :/

I Would really appreciate ur help!

---

### Post by shirilover on 2007-09-28
I would try using hplip instead.
```

sudo aptitude install hplip

```

Then, turn on your printer and try System->Preferences->HPLIP Toolbox
See if your printer is detected.
If not, Device -> Setup New Device
and follow the wizard.

My OfficeJet 4215 uses a USB connection and is detected once I turn it on, you may need to actually setup your printer if it uses the LPT port instead.

---

### Post by Shin_Gouki2501 on 2007-09-28
wow thx i try that!

---

### Post by Shin_Gouki2501 on 2007-09-28
hm sorry but neither:
sudo aptitude install hplip
nor
sudo apt-get install hplip
work it says that no packe could be found...ideas?

---

### Post by shirilover on 2007-09-28
Strange, it's listed in main. 
Another option would be to go to [http://hplip.sourceforge.net](http://hplip.sourceforge.net) and download the self-extracting archive with installer.
Then in a terminal, 
```

chmod +x hplip-2.7.7.run
sh hplip-2.7.7.run

```
The default choices are fine, then after it has finished
```

sudo hp-setup

```

---

### Post by Shin_Gouki2501 on 2007-09-29
i'm so really gratefull finally it did print the test page!
Thx a lot!
now .. just another question  :D
if i have a hp scanjet 2400
and:
[http://www.sane-project.org/unsupported/hp-scanjet-2400c.html](http://www.sane-project.org/unsupported/hp-scanjet-2400c.html)
its says tis unsupported so i guess no go with linux?
ot can the hplib hel there too?

---

