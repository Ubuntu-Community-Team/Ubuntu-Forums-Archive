---
title: "Curious about uninstall"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by nite owl on 2006-12-25
As a windows user for years and just in the last couple months made the switch to dapper, Im curious as to when you uninstall a program from Ubuntu is it completely removed like a purge??Or does it leave pieces of itself around like programs do in windows....I'm hopeing not :) If so does someone know of a command to completely purge???? Thanks in advance

---

### Post by pseudonym on 2006-12-25
> **nite owl said:**
> As a windows user for years and just in the last couple months made the switch to dapper, Im curious as to when you uninstall a program from Ubuntu is it completely removed like a purge??Or does it leave pieces of itself around like programs do in windows....I'm hopeing not :) If so does someone know of a command to completely purge???? Thanks in advance
From Synaptic Package Manager, just make sure the program is selected for 'complete removal' (or whichever it is).

From the command line, it's ```
sudo apt-get --purge remove <package name>
```
Note that these remove not only the package itself, but also any packages which depend on it. Packages that the program in question depended on are not removed. There is a program called deborphan which you can use to trace completely unused packages (eg. those which no other packages depend upon), but I've found it often likes to remove stuff you'd rather keep. It's really only necessary anyway if you're criminally low on disk space.

---

### Post by xyz on 2006-12-25
For a start check this out:
[Cleaning up all those unnecessary junk files...]("http://www.ubuntuforums.org/showthread.php?t=140920")
Run #4 at your own risk - may uninstall stuff you need as well.

---

### Post by nite owl on 2006-12-25
Hi thankyou for your prompt replies, These forums are really great. Thankyou to the Ubuntu/Linux community... :)

---

