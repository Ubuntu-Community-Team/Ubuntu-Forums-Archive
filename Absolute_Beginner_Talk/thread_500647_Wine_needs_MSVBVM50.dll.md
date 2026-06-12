---
title: "Wine needs MSVBVM50.dll"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by stuart62 on 2007-07-14
I am trying to run a windows.exe through Wine and I get the following error:

err:module:import_dll Library MSVBVM50.DLL not found.

I have this in /media/hda2/Windows/System32 folder.

New to Linux so don't know what I have to do to solve this problem.

---

### Post by BobCFC on 2007-07-14
when you are in your home directory click on the View menu and choose Show hidden files.

This will reveal lots of directories and files starting with a dot including .wine

Look around in there and you will find a fake c: drive and stuff.  put the dll in THAT windows folder not your real windows partition.

---

