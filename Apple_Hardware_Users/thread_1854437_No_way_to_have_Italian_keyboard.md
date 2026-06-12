---
title: "No way to have Italian keyboard"
date: 2011-10-04
forum: Apple Hardware Users
---

### Post by majortom67 on 2011-10-04
Hi to everybody. Here is Macbook Pro 6,2 (2010) with Kubuntu 11.10 b2 updated.
The original installation is OK but whenever I chose to update the system *as fot today are 334 new files) there is no more way to choose an Italin Keyboard (3rd option of the LOCATE / LOCATION panel in the System Settings (System Languages). Just two messages (I'll try my best to translate):

-  the System Language service doesn't supply a KCmodule interface with keyword "language/selector/selector.py". The factory doesn't allow the creation of such a component.
- there has been an error when you updated KDE and has been left back an old control module.
- There are still present old modules developed by 3rd parties.


TIA, any help is appreciated.
Simon

---

### Post by ankspo71 on 2011-10-06
Hi,
I think this is a bug that has already been reported here:
[https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/861930](https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/861930)

I have the same errors as you, and systemsettings crashed at the same time and the crash reporting service took me to the above page. 

I'm trying to find the bug at [https://bugs.kde.org/](https://bugs.kde.org/) but I can't find it. We might need to report it there.

As of now, my Kubuntu 11.10 beta 2 is fully updated, so you should be able to get your updates soon. I still have the same error as above  though. I'm sure future updates will fix this soon.

---

### Post by majortom67 on 2011-10-06
Here is how I solved: deleted .kde. Went into the panel below the screen and choose "configure" where there's the symbol of the language of the keyboard ("US" or "af" et etc). Went into the window of the keyboard's configuration and selected Intl 102 keys. Works fine. Of course, the error in the system setting is still there.

---

