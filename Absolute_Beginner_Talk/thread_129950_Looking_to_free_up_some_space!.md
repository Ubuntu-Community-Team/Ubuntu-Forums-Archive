---
title: "Looking to free up some space!"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by qwazert on 2006-02-15
My 4.2 Gb of harddrive-space is slowly vanishing...
By way of the Synaptic Packages, I removed several apps that I don't (or won't) use anymore. Is it safe to delete the folders (for those apps) that remain behind?

Any more ideas as to what I can jettison to free up some space?

---

### Post by mips on 2006-02-15
Uninstall packages you dont use via synaptic or apt.

Use the sudo **apt-get autoclean** & **sudo apt-get clean** to erase archive files. Might want to look at the apt-get documentation.

---

### Post by qwazert on 2006-02-15
What I meant to say was that I used the Synaptic to **Mark for complete removal** of said apps.
I was under the impression that this action removed them from my drive...is this not so?

---

### Post by Harleen on 2006-02-15
Your impression is right. Only some config files may stay on your drive, especially in the user's home folder.
But whenever you install a package from the net, a .deb file is downloaded and installed. This .deb file remains on your disc unneccessarily occupying space. The former mentioned commands remove them.
"apt-get autoclean" will remove all .deb packages, that are cached on your system, for which newer packages are already installed.
"apt-get clean" will remove all cached .deb packages.

---

### Post by xyz on 2006-02-15
The following helps me free up some space:
```
sudo apt-get install deborphan
sudo dpkg -P `deborphan
sudo apt-get remove --purge `deborphan`
sudo apt-get remove --purge `deborphan --guess-all`
```

---

