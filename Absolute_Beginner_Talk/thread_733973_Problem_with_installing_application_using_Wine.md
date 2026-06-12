---
title: "Problem with installing application using Wine"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by pkj on 2008-03-24
Hi,

Have just installed wine on Ubuntu Fiesty

However when i am trying to install an encyclopedia (originally for win platform) i am having the following problem

I am able to open the CD and select the installer.exe file

When i double click on it i am getting the following error

"Cannot open /media/cdrom1/QuickTimeInstaller.exe: No application suitable for automatic installation is available for handling this kind of file."

Am i doing something wrong <i am new to Wine>

Pls help

pkj

---

### Post by mikeyphi on 2008-03-24
Try Right-click on the installer.exe file - choose open with (wine if available) other.... find and select wine

If that fails - open a terminal and enter   wine /media/cdrom1/QuickTimeInstaller.exe

---

### Post by pkj on 2008-03-24
Thanks

It worked....

pkj

---

