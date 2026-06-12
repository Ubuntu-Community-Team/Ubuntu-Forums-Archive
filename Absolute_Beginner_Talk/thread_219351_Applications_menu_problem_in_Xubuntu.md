---
title: "Applications menu problem in Xubuntu"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by lewger on 2006-07-19
I recently installed Xubuntu on my PC and upon using it for the first time found it to be incredibly fast for my poor, old machine.  It ran flawlessly.  Unfortunately, it seems the "Applications" menu at the top doesn't want to open anymore.  Obviously I can still access the Internet, thanks to the small globe icon next to the "Applications" menu.  Any ideas/fixes?

Any advice is appreciated.

---

### Post by Kilz on 2006-07-19
> **lewger said:**
> I recently installed Xubuntu on my PC and upon using it for the first time found it to be incredibly fast for my poor, old machine.  It ran flawlessly.  Unfortunately, it seems the "Applications" menu at the top doesn't want to open anymore.  Obviously I can still access the Internet, thanks to the small globe icon next to the "Applications" menu.  Any ideas/fixes?

Any advice is appreciated.

[Its a known issue in the release notes, with a fix.]("https://wiki.ubuntu.com/XubuntuDapperReleaseNotes#head-b38e122d8c9dc3a3a68b3b1704231a9e90ca7361") It seems to happen to me when I try to use the menu editor.

---

### Post by OU812 on 2006-07-20
Hit alt+f2. In the run command dialog enter

xfce4-panel

I used this command in another distro when I did something silly that caused the panel - the bar at the top - to disappear. Also right-clicking on the desktop should bring up the applications menu.

john

---

### Post by lewger on 2006-07-20
@Kilz: Thanks, but considering I'm still a complete Ubuntu n00b, how exactly do I go about opening the terminal and removing the .xml file if I can't access the terminal through the "Applications" menu?  I might just need a thorough walkthrough here. :D 

@OU812: Thanks for the suggestions.  Unfortunately the run command did nothing but "refresh" the top bar itself, not the "Applications" menu, whereas I get no response whatsoever when right-clicking the desktop.

---

### Post by lewger on 2006-07-20
Nevermind folks, all is fixed.  ^_^  Had I simply bothered to look at similar threads in the first place I would've been set.  Thanks for the help.

---

