---
title: "Question about Wine"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by wcbardwell on 2007-08-14
I have 2 questions about wine:
1. Where are the icons? In the menu, all I have is an empty white box where the icons should be... Is there some way to get them?
2. Is it possible to have Wine automatically be associated with .exe files (My goal is to save a couple seconds and have my MS programs in my main menu and be able to load them without having to load "Wine File" and search for the .exe file).
Thanks!

---

### Post by Hospadar on 2007-08-14
1) If you right click on "Applications" and go to "edit menus", you can manually edit the launchers and choose icons for them.  The icons will be located probably where you installed the program (generally "/home/<your username>/.wine/drive_c/Program Files/whatever")
2) right click on an executable and go to "Properties" go to "Open With" go to "Add", "Custom Command" and type in "wine"

Also, you can open executables directly without using "wine file" from the command line.  just do a "wine executable_name_here.exe"

And if you make a custom launcher for an executable (for example to put on your desktop) the command you will want to use is "wine /the/full/path/of/the/file.exe"

---

