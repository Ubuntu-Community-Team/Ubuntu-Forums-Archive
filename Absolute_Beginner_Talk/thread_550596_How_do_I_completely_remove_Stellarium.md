---
title: "How do I completely remove Stellarium?"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by ElliottMarlow on 2007-09-14
I installed Stellarium today, and as I was adjusting the preferences (date, time zone, etc.), I accidentally changed the default perspective (or resolution?) to "fish eye" or something. Point is, now the entire sky is condensed into about a 4 inch circle, which makes opening up the preferences menu, or any other menu, impossible. I tried uninstalling and reinstalling, but that resolution setting seems to be "stuck." 

I tried sudo apt-get remove  --purge stellarium, sudo apt-get clean stellarium, and sudo apt-get autoclean stellarium, in various orders and rebootings, and when I try to reinstall it again, it always goes back to the fish eye view/resolution.

Obviously, I am not COMPLETELY removing Stellarium or else it wouldn't continue to "remember" that setting on reinstall. Is there some kind of registry I need to go to and delete entries from, in order to get a completely fresh install of Stellarium? Does anyone happen to know perhaps the keyboard shortcut (if one exists) to switch perspectives/resolutions?

---

### Post by swisscow on 2007-09-14
Have a look in the hidden folders in your home folder - there may be somewhere a folder called stellarium. Delete that.

---

### Post by ElliottMarlow on 2007-09-14
I found *.stellarium* in my home folder, and only deleted the config.ini file. Didn't even have to uninstall. Worked like a charm. Thanks!

---

### Post by swisscow on 2007-09-14
My pleasure - glad it worked! Pheewwwwwww!!!!!

---

