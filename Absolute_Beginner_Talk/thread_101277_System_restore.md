---
title: "System restore?"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by PheonixRising on 2005-12-09
Hi, I just uninstalled Windows (it was being glitchy) and installed Ubuntu on my PC. However, being the Linux noob I am, I installed some really weird crap on my system and I don'y know where I can find it. So I was wondering if there is a system restore function like the one in windows.

---

### Post by earobinson on 2005-12-09
in synaptic under file->Histroy (I think windows :() It should list everything you installed and when so you can uninstall it. I dont know of any undo the last 24 hours features, but it a great idea.

---

### Post by PheonixRising on 2005-12-09
See, the thing is, I used Wine to install Windows game on my computer, and I can't play it, so now I want to uninstall it. Since I can't find it, I'm not sure how I can uninstall it.

---

### Post by earobinson on 2005-12-09
you could run the uninstaller using wine

---

### Post by PheonixRising on 2005-12-09
That's the problem, it doesn't show up in the uninstaller for some reason.

---

### Post by earobinson on 2005-12-09
I think you miss understand me, In windows when you install an program in the same dir that it is installed it usualy has an uninstall exe. When you install a program with wine this is the same case, so you should be able to run that uninstaller with wine and uninstall it.

What game is it? This may help (some really old games do not have uninstallers and you can just deleat the program and be done with it)

Also worst case you remove and reinstall wine and everything is fixed, **you will not have to reinstall ubuntu**. Linux is very robust :)

---

### Post by KingBahamut on 2005-12-09
you could always go to a command line and 

cd /home/<yourusername>/.wine/drive_c/ 

Youll find your folder heirarchy for wine in there , to resemble the windows file hiearchy. 

Cd to the directory with the game you want to remove , 

rm nameofdirectory -fr 

Be sure to be careful with the rm -fr command, it can be unweildy if your not careful and damage your system.

---

### Post by earobinson on 2005-12-09
This is true, I was going to wait to suggest that because im not sure how wine deals with registry keys.

---

