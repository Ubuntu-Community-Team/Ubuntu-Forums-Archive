---
title: "RealPlayer Troubles"
date: 2005-11-01
forum: Absolute Beginner Talk
---

### Post by VladTheImpaler on 2005-11-01
I followed the installation instructions in several of the threads here and thought installation was successful.  RealPlayer 10 was installed to /usr/share/RealPlayer and the files are there.

When I click the RealPlayer 10 icon in the Sound and Video menu, I get:

Cannot Launch Entry
Details:  Failed to Execute Child Process "realpay" (no such file of directory)

What did I do wrong?

---

### Post by thinhlegolas on 2005-11-01
[QUOTE=VladTheImpaler]I followed the installation instructions in several of the threads here and thought installation was successful.  RealPlayer 10 was installed to /usr/share/RealPlayer and the files are there.

When I click the RealPlayer 10 icon in the Sound and Video menu, I get:

Cannot Launch Entry
Details:  Failed to Execute Child Process "realpay" (no such file of directory)

What did I do wrong?[/QUOTE]

It's simply because /usr/local/RealPlayer/realplay is not in the path

You should do this

export PATH=$PATH:/usr/local/RealPlayer/

or

ln -s /usr/local/RealPlayer/realplay /usr/bin

---

### Post by VladTheImpaler on 2005-11-01
Thank you, thinhlegolas!

---

