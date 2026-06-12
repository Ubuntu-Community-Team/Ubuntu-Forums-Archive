---
title: "[SOLVED] kTorrent works in KDE, but reports &amp;quot;invalid tracker data&amp;quot; when run in GNOME."
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by jw5801 on 2007-09-14
Hmm... I'm confused! I have both KDE and GNOME desktops on my system. kTorrent runs perfectly under KDE, but when I run it under GNOME, I can't connect to any trackers, it just returns an "invalid data from tracker" message in the tracker status field. It's not the tracker that's down as it doesn't do this under KDE (I can alternate back and forth) and several trackers all report the same thing.

Cheers for any enlightenment anyone can give!
Jason

---

### Post by chuckyp on 2007-09-14
ktorrent works fine here in Gnome maybe you have some sort of firewall running when using gnome?

---

### Post by jw5801 on 2007-09-14
Not that I'm aware of... that's what my router's for. And yes the port I'm using is forwarded through. Would there have been one put in place when I installed? And how would I check?

---

### Post by jw5801 on 2007-09-14
Success! My global network proxy was set to an automatic configuration url. Apparently in KDE kTorrent managed to ignore the global settings like I told it to, but not in GNOME. Oh well problem is all solved now!

---

