---
title: "Interface gone"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Pconfig on 2007-06-13
Hello,

i installed Ubuntu for the first time yesterday. It all worked nice (better then i expected) and i got everything working pretty good.

Now tomorrow i was trying to get my Bluetooth keyboard and mouse working. Took me some time but after that they worked. Now i had to edit something in a file (etc/default/bluetooth) to get the mouse and keyboard connected at a restart. Ok .. Edited the file, saved and rebooted. After the reboot it seems that my bar with the clock and such is gone. 'The top and bottom bar'. Don't know how it's called in linux terms :)

Anybody knows what might be the problem?

Thanks
Thomas

---

### Post by tchoklat on 2007-06-13
Boot into your normal Gnome session. (the one without the panels) Hit Alt-F2. In the run dialog that pops up enter, "gnome-panel" without the quotes, and hit enter. That should have started one for you. Now you can right click on that panel and add another one if you want. Be sure to go to System->Preferences->Sessions and save your session so that the panels will show up the next time you login. (STOLEN FROM ANOTHER POST)

---

### Post by Pconfig on 2007-06-13
This gives me: I've detected a panel alreadry running, and will now exit.

Hmm. It's not visible anyway :(

---

### Post by Pconfig on 2007-06-13
> **Pconfig said:**
> This gives me: I've detected a panel alreadry running, and will now exit.

Hmm. It's not visible anyway :(

Ok, for some reason it does work again now. I've just been pressing some buttons and trying some things out. Don't really know what fixed it.

Seems like my bluetooth isn't working correctly. The mouse and keyboard don't connect automaticly. I always need to connect them with hidd --connect :s
(Even though i edited the bluetooth file)

---

### Post by Pconfig on 2007-06-13
For the record, this thread fixed my Bluetooth problem:
[http://ubuntuforums.org/showthread.php?t=447637&highlight=bluetooth+keyboard](http://ubuntuforums.org/showthread.php?t=447637&highlight=bluetooth+keyboard)

Thanks and cya soon (when i screw something else up :D)

---

### Post by Pconfig on 2007-06-14
I keep getting the same problem with my menu bars. At first they magicaly disappear and then when i reboot a few times they're back. Does anybody have any idea on what might be happening?

---

