---
title: "Wine"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by Nhatz on 2007-01-15
HELP! anybody teach me how to use wine.... PLEASE!!!:confused:

---

### Post by Pobega on 2007-01-15
Let's take it from the start.

In Windows you use an installer to install a program, correct? So in the same fashion you'd use Wine to install the program. So download foo-setup-3.exe and put it on your desktop. Now, go to the command line:

> cd ~/Desktop
wine foo-setup-3.exe

Everything will claim to install to c:\Program Files\ like normal, but it's actually in ~/.wine/drive_c/Program Files/. Now in the same way you ran the install, you run the executable.

> cd ~/.wine/drive_c/Program\ Files/foo
wine bar.exe

---

