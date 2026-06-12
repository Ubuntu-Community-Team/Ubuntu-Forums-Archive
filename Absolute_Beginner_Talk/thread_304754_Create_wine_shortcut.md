---
title: "Create wine shortcut?"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by baysl on 2006-11-22
When I want to run a program I have to 
open terminal an write:

wine ~/Ewb512/EWB512/WEWB32.EXE

How do I create desktop shortcut for this program?

---

### Post by Circus-Killer on 2006-11-22
well, in the create launcher window, under command you would have something like:

> wine 'C:\Program Folder\filename.exe'

remember that all programs get installed in a mock c: folder in your home directory. however, when running the wine command, you can use the windows-style pathname to point to your program.

---

