---
title: "KDE wallpaper installer previews"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by editrix on 2006-08-06
Since the latest updates trashed my wallpaper, I've been trying to find a new one. If I click on "get new wallpapers" in control centre, I can preview all the ones in the Highest Rated list, but not the ones in the other two (Most Downloads and Latest). If I click on any of them, a progress window briefly flashes as if downloading it, but all I can see is the last preview I looked at in the Highest Rated list.

Also after those upates, I got a message about a kdmrc problem
[http://www.ubuntuforums.org/showthread.php?t=230411](http://www.ubuntuforums.org/showthread.php?t=230411)

Could that be causing the problem here?

---

### Post by titoose on 2006-08-12
Same problem here. Superkaramba theme selector with this problem too. In addition, I have kwin crashes since kde 3.5.4 update and font problems in some apps (not only in GTK ones).

---

### Post by editrix on 2006-08-12
> **titoose said:**
> Same problem here. Superkaramba theme selector with this problem too. In addition, I have kwin crashes since kde 3.5.4 update and font problems in some apps (not only in GTK ones).

Ah well. Maybe with two of us, we'll get some answers :-)

It seems the fonts are always grey and blurry when I'm root: Synaptic, Kate (editing a file as root), etc. Haven't got Superkaramba installed but I doubt that's the diff. If you want the original wallpaper back, a friend on Debian sent me his.

---

### Post by editrix on 2006-08-12
Found a solution to the fonts problem:

[http://www.ubuntuforums.org/showthread.php?t=234420](http://www.ubuntuforums.org/showthread.php?t=234420)
> No antialiasing in GTK apps after recent KDE upgrade - solution
I thought it could come in handy for some users if I post this. Maybe it was mentioned before, but I couldn't find it here.

After the upgrade to KDE 3.5.4 (from 'latest' Kubuntu repository), I've lost antialiased fonts in GTK applications for no apparent reason, and nothing I thought of seemed to work. But today I've finally found the solution - it seems to be some kind of bug in KDE and there's an easy workaround: Go to Font settings and change the General font to any font other than the one you had set before. Voila, GTK apps appear fine. You may now set the General font back to your favourite one, the problem is gone.


But the wallpaper thing still won't work.

---

### Post by titoose on 2006-08-13
Font problem solved, thank you, but I still can not select wallpapers from "most downloaded" and "latest" tabs.

I had to make a desktop launcher with a "kwin --replace" because the kwin crashes continue. I'm thinking to downgrade to KDE 3.5.3.

---

