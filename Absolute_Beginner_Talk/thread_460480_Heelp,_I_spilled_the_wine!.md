---
title: "Heelp, I spilled the wine!"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by flavio newbie on 2007-05-31
I uninstalled wine, and i also deleted the content of home/flavio/.wine and then i installed again wine, but c: and z: are not there anymore... Help!

---

### Post by AAM on 2007-05-31
Firstly, have you run wineconfig in the terminal to set it up? If this doesn't help, completely uninstall WINE (there are two uninstall options in the package manager) and then start again.

Second thing ... learnt anything? Why all the uninstall/install activity?

---

### Post by coffeecat on 2007-05-31
~/.wine, and c: and z: will be recreated the first time you run wine. Based on this, a useful tip if you make a complete mess of wine configuration and want to start again, is to do what you did and delete ~/.wine. Of course, this will delete any Windows programs you installed but at least you can start over fresh.

---

### Post by flavio newbie on 2007-05-31
I'm opening Wine File but there is nothing yet... i also tryed to run an .exe program but nothing seems to happen (open with /usr/bun/wine)

---

### Post by coffeecat on 2007-05-31
/usr/bin (not bun :wink:) is in your $PATH. So to run wine just type 'wine' in a terminal - you don't need the full path.

As far as I remember just run 'wine'. That will create ~/.wine and return you to a prompt very quickly. Then run 'wine file.exe' and take it from there.

---

### Post by flavio newbie on 2007-05-31
Thanks a lot guys, everything is working again!

---

