---
title: "Kopete and random KDE 3.5 question"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by Imsati on 2006-11-06
Yeesh, I leave KDE for 10 days and I return a total n00b...

Recently re-installing Kubuntu after some hardware tweaks, I decided to burn a new .iso (thinking/hoping that KDE 3.5 would be a part of it, but more of that in a moment). After setting up Kopete for use with AIM, when I sign on, it shows my groups of buddies, but doesn't show any names. For example, I can see the 'Friends' group, but the Online/Offline ratio comes up as 0/0, though when I go into settings, I see everyone screen name that should be on the list. Any info with that? I could use GAIM, but I like Kopete better.

About KDE 3.5. I tried to upgrade earlier this evening, but something went wrong 1/2 way through and it wouldn't work. I added the deb package to my Adept, applied, and fetched updates. Is that the wrong way? Should I try something else or was the mess up just a fluke?

I better get back on my Linux game quick! Thanks for pointing me in the right direction!

~Jay

---

### Post by Imsati on 2006-11-06
With the KDE upgrade, the download goes fine, but the installation stops at 66% (configuring the new version of kdm). The specific error title is 'Could not commit changes' and the message is "There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages."

Any ideas?

---

### Post by jpeddicord on 2006-11-06
I am not sure about the strange Kopete bug; try looking for an option in the menus for Show Empty Groups.

As for the update error, everything should be fine with just trying again. If a package fails to download halfway, it will automatically try to resume it later. EDIT: Sorry, I just now saw the second post. Working on it.

EDIT2: Try running this:
```
sudo apt-get install -f
```and then try installing KDE again.

Jacob

---

### Post by Imsati on 2006-11-06
That seemed to do it. Just looke under Help andmy KDM version is now 3.5.5

Thanks! Kopete just clicked on as well. Something I tried 4 times previously miraculously worked. I think I'm going to do a fresh install incase it didn't load properly.

Thanks again for the assistance!

---

