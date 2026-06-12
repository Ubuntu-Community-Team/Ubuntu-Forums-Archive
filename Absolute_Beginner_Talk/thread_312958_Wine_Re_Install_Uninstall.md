---
title: "Wine Re Install Uninstall"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by ddbann on 2006-12-05
Previous install of wine worked fine. Now on my desktop instead of a CD logo for the cd in the drive it's a external drive with a cd sticking out of it for a logo. clicking on the desktop logo doesn't say open with wine but if i 
open the cd and click on the setup it says open with wine windows emulator.
it starts the windows installation and opens a desktop up but than nothing else happens.

should i uninstall wine and reinstall. how do i do that?

---

### Post by bodhi.zazen on 2006-12-05
I would downgrade your wine install.

[Downgrade wine](http://doc.gwos.org/index.php/HowToWine#Downgrade_wine)

With wine, once I get it up and running the way I like, there is no need to run the newest/latest.

---

### Post by ddbann on 2006-12-05
Remove the new wine (use synaptic, apt-get, or aptitude).


what do I type to remove wine by way of the terminal?
it won't let me install an older version because it says a newer version is already installed

---

### Post by echo $USER on 2006-12-05
If you want to completely uninstall, reinstall you need to purge the config files like...

> sudo apt-get remove --purge wine
> sudo apt-get install wine

---

### Post by ddbann on 2006-12-05
ok i have uninstalled wine. when i open up a windows program cd and right click on setup.exe the open with wine option is not there.

---

### Post by bodhi.zazen on 2006-12-05
re-install wine, then log-out and back in to update your menu options.

---

