---
title: "language in wine"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by jwalters on 2007-08-03
trying to install 'call of duty' in wine, but the wine program opens in (perhaps) Japanese...
I have uninstalled/reinstalled the program......and the same thing happens.
don't have a clue as to how to totally erase and get a whole new version of 'wine'...nor can I change the language

I've checked the other threads and can not find help..........help??

---

### Post by benx009 on 2007-08-03
how exactly are you installing wine?  through synaptic?

---

### Post by Hospadar on 2007-08-03
well if you want to totally remove wine (whether you installed it from the fiesty repositories or from wine's own repo at budgetdedicated) you would want to do ```
sudo apt-get --purge wine
``` this will remove wine as well as all the configuration files, if you want to further get the job done, you'll want to delete the ".wine" directory in your home directory (if you use the gui to do this you'll have to go to view->show hidden files) this will remove any applications/fonts/anything that you installed with wine on that account as this contains the "C:\" drive for wine.

That said, you should probably first look around for some guides as to  installing call of duty, there may be some command line option you need to add to the launcher to specify the language, or you may need to find some windows font and install it (you can just copy them over from a windows installation, or find them online, put them in .wine/drive_c/windows/fonts.

Also, make sure you have the package msttcorefonts installed, this has a lot of basic ms fonts and I know with some games this will have the fonts you need.
```
sudo apt-get install msttcorefonts
```

---

### Post by jwalters on 2007-08-03
Thank you I finally got wine to recognize english.............but call of duty is not loading from the 2 cd's..........It will load the first cd and then when I exchange for the second it will load no further. Any ideas?

---

