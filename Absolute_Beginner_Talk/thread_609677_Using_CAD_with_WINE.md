---
title: "Using CAD with WINE"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-11-11
I appear to have successfully installed version 0.9.49 of WINE into Gutsy 7.10.

I am hoping that I can now install IntelliCAD 4 ( from [http://www.cadopia.com/](http://www.cadopia.com/) ) which is intended to run on XP and would appreciate it if someone who has done this, or who knows how to do this, could give me some advice.

Thanks.

---

### Post by P4man on 2007-11-11
This guy got 6.2 working without problems it seems:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7434](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7434)

Just run the installation executable and hope for the best :) Run it from a terminal so you can catch any error messages:

```
wine /path/to/installationfile/name_of_installation_file.exe
```

If it worked, you can launch it simply from the gnome menu,  applications / wine / program files.

---

