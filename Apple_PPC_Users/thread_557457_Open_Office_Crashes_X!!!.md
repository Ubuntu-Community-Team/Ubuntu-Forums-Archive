---
title: "Open Office Crashes X!!!"
date: 2007-09-22
forum: Apple PPC Users
---

### Post by lotu5 on 2007-09-22
I'm so sick of openoffice crashing that I'm installing neooffice on the macosx side of my machine. It really saddens  me because I want to spend more time in linux on my machine, but openoffice is intolerable. 

So here's my problem, about 50% of the time when I click on a menu item in openoffice, it causes X to hang. Sine the input is taken and held by X, the only option is to hard reset the machine. Ctrl-alt-delete doesn't help. I'm using parallels, and I don't see any way to send a ctrl-alt-backspace. 

Does anyone else have this problem? I'm using ubuntu feisty fawn, the latest version, with all the latest updates. This must be happening to lots of people right? 

I tried to submit a bug at openoffice.org, but you have to register to submit bug forms and I don't want to do that.

---

### Post by Techpenguin on 2007-09-22
try a different open office version?

---

### Post by adrianbowyer on 2007-09-26
Check out:

[http://ywwg.com/wordpress/?p=76]("http://ywwg.com/wordpress/?p=76")

To quote:

symptom: when starting openoffice.org, the program loads, the main window comes up, and XWindows freezes. The mouse still moves, but no input is received and any moving graphical elements like stripcharts or xmms title freeze.

Explanation: you have an nvidia card, and have enabled XRENDER acceleration. When OO.o tries to do its internal font smoothing, something screws up in the acceleration.

Soltution: Experimental video acceleration options, how naughty! Turn off XRENDER acceleration, or disable font smoothing in OO.o somehow.

---

