---
title: "I can't find where Package Manager installed something..."
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2007-01-14
What's the default for Ubuntu's package manager. I download a Linux version of a game, and i chose to open it with package manager. It installed it, but didn't tell me where.

Where is its default?

---

### Post by obsidion on 2007-01-14
> **Captain Kirk76 said:**
> What's the default for Ubuntu's package manager. I download a Linux version of a game, and i chose to open it with package manager. It installed it, but didn't tell me where.

Where is its default?


   Depends on how the package was written, there is no default as such. In what form was the package and where did you get it from. This basic information will help us to help you.

---

### Post by Captain Kirk76 on 2007-01-14
The file had the extension .deb, and was the game OpenTTD For Debian/Ubuntu.
If it helps, you can download the package yourself from the website [http://openttd.com/downloads.php](http://openttd.com/downloads.php) and clicking on the latest release one, and the debian and ubuntu.

---

### Post by rabid9797 on 2007-01-14
if you used a .deb it should be under applications -> games

but if it isn't there try typing "OpenTTD" in the terminal

---

### Post by Captain Kirk76 on 2007-01-14
I would, except for part of the installation, i need to edit one of the files, and copy a file to the space where it is installed.

---

### Post by kerry_s on 2007-01-14
use synaptic, just find the package you installed and click on it to high lite, then click properties, than installed files tab.

or from command line run->

sudo updatedb

locate (name)

---

### Post by obsidion on 2007-01-14
It installs here

/usr/share/games/openttd

---

