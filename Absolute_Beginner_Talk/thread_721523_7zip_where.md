---
title: "7zip where?"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by faraz_k86 on 2008-03-11
I downloaded 7zip using the add/remove panel and it got installed but it is nowhere to be found?? where can it be ?

---

### Post by Crafty Kisses on 2008-03-11
> **faraz_k86 said:**
> I downloaded 7zip using the add/remove panel and it got installed but it is nowhere to be found?? where can it be ?

Have you tried running 7zip through the Terminal?

---

### Post by Therion on 2008-03-11
It's integrated into the command line and the context menu.  

If you want to compress a file, right-click on it.  If you want to decompress a file, right-click on it.

---

### Post by Sokraates on 2008-03-11
Usually installed programs should appear in one of the menu under "Applications". If it's not there, you can add an entry through one of the applications in the "System"-menu. I'm sorry, I don't recall which one.

If you don't find a 7zip menu entry and don't know how to add the entry but want/need to use it quickly, you should best start the terminal and start 7zip from there. Typing "7zip" should do the trick.

---

### Post by rudihawk on 2008-03-11
maybe open the terminal and type: 7zip and hit enter...?

---

### Post by bobbocanfly on 2008-03-11
7z support on Ubuntu is a little sketchy. ([See Launchpad Bug #122935 ]("https://bugs.edge.launchpad.net/ubuntu/+source/p7zip/+bug/122935")).

To use it run

```
sudo apt-get install p7zip-full
```

Then open up your 7z file in file-roller and it should work.

Edit: Also the package lzma might be useful (sudo apt-get install lzma).

---

