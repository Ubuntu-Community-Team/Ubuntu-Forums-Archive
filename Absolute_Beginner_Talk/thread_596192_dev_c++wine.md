---
title: "dev c++/wine"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by amtnbiker16 on 2007-10-29
i used wine to install dev c++ on my gutsy laptop and it works fine for the most part, but when i try to run my program, the execution window never opens.

i know that dev c++ isnt the greatest compiler around, but I'm using it for a class because i want to make sure my programs are compatible when i turn them in

im not entirely sure what the problem is with it.  It compiles fine and im not having any other problems whatsoever.  i dont know if it is a problem with the window staying open or what, but its NOT a problem with my source code, i already checked
maybe its wine not wanting to open the second window, i cant really tell

anyway, id appreciate the help

---

### Post by Hospadar on 2007-10-29
how are you trying to run the program? you will probably need to run it with wine just as you run dev c++ with wine.

I would hiiighly suggest switching IDE/compilers to something native for linux (eclipse/g++, anjuta/g++, kdevelop/g++) and writing and testing your code their, and then testing it on a windows machine (surely there are some windows computer labs somewhere)

Unless you are in a really advanced class, it seems highly unlikely that any of your code would run/compile on linux but not on windows.

For that matter, I think dev c++ uses the exact same compiler as linux uses, so there should be even less issues.

---

### Post by hangar_18 on 2007-10-30
just open your compiled exe like this -> right click -> open with -> other -> write wine, click 'Run in terminal' and another 2 options,
before doing this you will probably need to get cmd.exe work in wine,
i just copied 'system32' and 'system' folders from my xp (make backup before doing that!)

---

