---
title: "Wine doors error"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-01-27
I am using Wine doors with Gutsy x64.

glade@Muzic-Jukebox:~$ wine-doors
Started logging session
Checking wine drive: /home/glade/.wine/
wine.py: CheckDrive: No wine-drive defined in specified wineroot

On doing this, I get a window showing "Welcome to Wine Doors" and asks me to enter my name, company and a checkbox for "I have a valid windows licence". No matter what I enter, when I press Proceed button, it freezes for 2-3 seconds, the buttons become inactive and the window freezes forever. How do I proceed?

---

### Post by ureckifix on 2008-01-27
Not to be smart but did you get the 64 bit D/L

---

### Post by sayakb on 2008-01-29
> **ureckifix said:**
> Not to be smart but did you get the 64 bit D/L

Yes, I got the 64-bit Gutsy download from getdeb.net
(The package info said amd64 architecture :D)

---

### Post by mikeyphi on 2008-01-29
> **LinuxIsInnovation said:**
> I am using Wine doors with Gutsy x64.

glade@Muzic-Jukebox:~$ wine-doors
Started logging session
Checking wine drive: /home/glade/.wine/
wine.py: CheckDrive: No wine-drive defined in specified wineroot

On doing this, I get a window showing "Welcome to Wine Doors" and asks me to enter my name, company and a checkbox for "I have a valid windows licence". No matter what I enter, when I press Proceed button, it freezes for 2-3 seconds, the buttons become inactive and the window freezes forever. How do I proceed?

I'm not familiar with the 64bit OS or Wine-doors...but two questions
1 do you have a folder drive_c in /home/glade/.wine?
2 did wine.py come from the wine-doors install (I only ask since .py is a python extension and I'm surprised to see it there)

It would seem that wine-doors is looking for a drive under wine.py  - in the 32bit OS, the drive is in the Home/user/.wine folder

---

### Post by Kilz on 2008-01-29
If you have never started wine it will not setup its .wine folder in your home folder. Open a terminal and type in wine or winecfg.

---

### Post by sayakb on 2008-01-31
I use Wine regularly.. IPMSG32.exe is a LAN file sharing Windows app that I use with Wine. I do have a drive_c in the .wine folder in my home folder.
And, I cant say about the wine.py , very less knowledge in this regard :D

---

