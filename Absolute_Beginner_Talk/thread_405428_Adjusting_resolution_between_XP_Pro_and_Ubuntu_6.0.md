---
title: "Adjusting resolution between XP Pro and Ubuntu 6.06"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-04-09
Set up my computer as a dual boot between XP Pro and Ubuntu 6.06. How do I resolve the resolution differences between the two OS's? If I adjust my monitor for one it throws off the other. Both are 1024 by 768.  Also, how do I single click to open a file or folder rather than the default double click?

---

### Post by kyphi on 2007-04-09
Resolution settings are operating system specific.

In an Ubuntu terminal type

sudo dpkg-reconfigure -phigh xserver-xorg

on the ensuing screen use your up/down keys to scroll to the resolution you want and then select it by pressing the spacebar.  Then enter and exit.

Then log out and back in.  Done.

I assume that you know how to change resolution in XP.

---

### Post by jacatone on 2007-04-09
How does this differ from the System/Preferences/Screen Resolution button in Ubuntu?

---

### Post by kyphi on 2007-04-09
This way you can expand the resolution listing in System-Preferences-Screen resolution to give you more choice.

---

### Post by jacatone on 2007-04-09
Tried it several times and just got a "Command not found" result. I have one of those integrated 3D graphics cards which I guess mean it's part of the motherboard like a winmodem?

---

### Post by kyphi on 2007-04-09
There is a space before "-phigh".

Do you have an LCD or a  CRT monitor ?
What resolutions do you want for either of your operating systems ?

I run a dual boot system between Ubuntu 6.06 (Dapper) and XP.  The resolution for Ubuntu is set to 1280x1024 and XP to 1024x768.  There are no problems.  I use an LCD monitor. 

XP has a command line too but I don't think that Microsoft wants it publicised.

---

