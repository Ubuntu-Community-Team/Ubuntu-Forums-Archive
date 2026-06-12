---
title: "poppler update has &quot;can't be authenticated&quot; warning"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-08-08
The Update Manager is showing three updates are now available: libpoppler1, libpoppler1-glib, and poppler-utils. The update is from version 0.5.4-0ubuntu8 to version 0.5.4-0ubuntu8.1

But when I go to udate, I get: "Warning - You are about to install software that can't be authenticated! Doing this could allow a malicious individual to damagae or take control of your system."

Well that sounds bad, but what should an Absolute Beginner do next then? It looks like my system is asking for the update, then warns me away. Shouldn't there be a third step that breaks the cycle? What am I being blind to here?

Checking online shows 0.5.4-0ubuntu8.1 does indeed exist in official form. 
[http://packages.ubuntu.com/feisty/text/poppler-utils](http://packages.ubuntu.com/feisty/text/poppler-utils)

---

### Post by starcraft.man on 2007-08-08
Right, I just updated those today or was it yesterday? Anyway, that's a weird message. I don't think I got it so let's just try something... open a terminal please. That can be done from Applications Menu > Accessories > terminal. Then type what I put in the boxes and push enter:

> sudo aptitude update

> sudo aptitude upgrade

Then it should tell you your going to upgrade 3 or so packages. Type in "y" and then push enter if no error or other worrisome message pops up. If your not sure, push "n" and enter and copy paste the message here. Shouldn't give you trouble though so that should do it. Oh and if you want to know more about those two commands read the guide (linked in blue) in my sig, have fun :).

---

### Post by ofb on 2007-08-08
Or, just fire up Synaptic and hit Refresh. At least that's what I just did, and Update Manager was then able to proceed without the unauthenticated software warning.

Okay, good, but why?

What wasn't refreshed that caused the warning? Shouldn't Update Manager have gotten that information in the first place?

---

