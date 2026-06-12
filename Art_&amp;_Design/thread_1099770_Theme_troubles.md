---
title: "Theme troubles"
date: 2009-03-18
forum: Art &amp; Design
---

### Post by wigmoso on 2009-03-18
Ive been trying to get this theme set working for about 5 hours now. Splash screen works, skins for media player are cool, but for the general ubuntu theme everything sucks and google has failed me (although i fully expect to get owned by someone with a perfect link to my question) so help me plz!

Emerald does absolutely nothing.
That basically sums it up.

I tried loading tar.gz's in there which just didnt work (i saw somthing like that suggested somewhere), so i extracted the .emeralds and imported them, it looked in order but nothing happened so i ctrl+alt+backspaced and.. well.. there is no "and" nothing happened except for the human theme startup.

I've tried 5 different themes, even spammed all 5 into emerald at the same time, to no avail.  But luckily for me i'm a noob and whatever i screwed up is probably obvious and therefore easy to fix.

---

### Post by mcduck on 2009-03-18
Are you actually *running* Emerald? Run "emerald --replace" to reload it after changing the emerald theme.

Also note that emerald only affects your window borders, nothing else. You need to use GTK2 themes to change how the programs look like.

---

### Post by gabbman on 2009-03-18
When I close the terminal, the window decoration vanishes.

---

### Post by oedipuss on 2009-03-19
I'd suggest using fusion-icon (it's in the repositories) for an easier way to manage emerald and compiz. Basically a tray icon with launchers and options for window managers and decorators. You'll find it at Applications/System Tools, after you've installed it.

If you still need to run emerald from a terminal, try "disown emerald" after you run emerald, or just "disown" if emerald is the only thing you've executed in that terminal. (I just found this command, I'm not sure if there are any disadvantages)
Or simply run it from an Alt+F2 dialog ("Run Application"). 

Apart from that, I believe emerald isn't developped any more. There's a new decorator in the works, but nothing usable yet, I think. I'd suggest going with the default metacity decorator that comes with compiz, even if it makes some themes unavailable.

---

### Post by mcduck on 2009-03-19
> **gabbman said:**
> When I close the terminal, the window decoration vanishes.

You need to change the default window decorator to Emerald in Compiz settings. Open CompizConfig Settings manager (install it if you haven't got it), go to Window Decoration-plugin and change the decorator command to "/usr/bin/emerald".

If you need to run "emerald --replace", for example to apply new theme, I recommend pressing Alt-F2 and using the Run Command -dialog instead of a terminal. This way you don't have to worry about the decorator closing again if you close the terminal you used to start it.

---

