---
title: "Can't install Steam"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Mikestarko on 2007-05-22
I have wine installed and downloaded the steam .msi file.  I pasted it in home/*myname*, went to terminal and typed "wine /home/*myname*/SteamInstall.msi"

It said bad exe format.  Anyone know what I can do?

---

### Post by Ek0nomik on 2007-05-22
Try

```
wine msiexec /i xyz.msi
```

---

### Post by DUNC4N on 2007-05-22
I'm gonna try that, I copied all the stuff off of the disk, but played around too much during the install. While downloading the update for CSS, I froze, and My steam Icon disappeared.

Now I can't uninstall steam, or run steam...

---

### Post by Ek0nomik on 2007-05-22
[http://www.linuxforums.org/forum/wine/9914-installing-steam-wine.html](http://www.linuxforums.org/forum/wine/9914-installing-steam-wine.html)

[http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

I don't feel as though I have much luck with Wine, but on this WineHQ page it seems everything always works.

---

### Post by justin whitaker on 2007-05-22
What I would do, if you are averse to paying for Crossover Office, is use the trial version to install Steam, then use regular Wine to execute it. ;)

---

