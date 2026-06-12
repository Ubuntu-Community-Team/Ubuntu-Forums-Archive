---
title: "problems with firefox"
date: 2005-09-23
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-09-23
Sometimes when i open firefox, i get the message that my default profile is being used and cannot be opened.  In these cases, i end up opening another profile that i would create.  Is there a way to fix this problem?

---

### Post by KingBahamut on 2005-09-23
youve got firefox running somewhere. 

Open up your system monitor in System tools, find it, kill it, and try again. 

Alternately , youll find that Thunderbird will do the same thing.

---

### Post by SilentCacophony on 2005-09-23
That seems to me to be a problem with firefox itself, as it's happened to me on the windows version in the past.

Generally, it's because firefox is still running in the background, and won't open twice on the same profile.

Use your favorite process-killer to kill it first. For example in gnome, run the system monitor (under applications > system tools,) select firefox-bin, right-click, and select kill process. There are many ways to kill apps from the commandline as well, including top and htop.

EDIT: I'm a lousy typist ;)

---

### Post by canadianwriterman on 2005-09-23
I've also had the same problem from time to time. According to advice on the Firefox forums, one way to ensure that Firefox does not continue running in the background is to close it from the "File" menu, rather than just clicking on the "X" in the corner to close it.

---

### Post by Wolki on 2005-09-23
[QUOTE=racermike1967]Sometimes when i open firefox, i get the message that my default profile is being used and cannot be opened.  In these cases, i end up opening another profile that i would create.  Is there a way to fix this problem?[/QUOTE]

Sometimes after firefox crashes it'll still claim to access the profile, though it doesn't anymore. In that case, delete the "lock" file in your profile directory.

---

