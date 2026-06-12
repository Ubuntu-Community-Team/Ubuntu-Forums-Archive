---
title: "Steam problem"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by underworld288 on 2006-06-29
I know this is probably a simply poblem but here it goes, when i go to open up the steam.exe file it says "Please turn off compatibility mode". I would know how to do this in Windows but in Linux im stuck.

---

### Post by shoot2kill on 2006-06-29
are you using WINE or CrossOver-Office, or any program like that...?

---

### Post by underworld288 on 2006-06-29
yes wine

---

### Post by shoot2kill on 2006-06-29
i never used steam.. what would u do with this error in WIN

---

### Post by underworld288 on 2006-06-29
you would simply right click on the .exe file go to properties, go to the compatibility tabe and turn compatibility off.

---

### Post by Jasper Houtman on 2006-06-29
check if wine is set up to emulate a certain version of windows for steam.
Start up your terminal (applications > accessories > terminal)  and type: winecfg
Then click on the applications tab and look for an entry for steam.
If it's there then select it and click on remove.

If that doesn't help than check [here]("http://appdb.winehq.org/appview.php?versionId=1554") if you installed correctly (or for a fix to your problem).

---

### Post by underworld288 on 2006-06-29
ok nevermind i fixed it, i went into the terminal went into winecfg and it was set to run in compatibility for windows 98, i changed it to windows 2000.

---

### Post by Jasper Houtman on 2006-06-29
If you have any other problems with running steam than just click on the link in my previous post (links to a wine page about running steam). There's a list of fixes in there for common problems.

---

### Post by underworld288 on 2006-06-29
ok ill do that if i get any other problems

---

### Post by underworld288 on 2006-06-29
ok i went to [this]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games") site and was looking at the troubleshooting section, because when i start steam (at the updating part) it stops at 26%. I was looking at this site and the advice given for this problem, the code for the terminal is at the site but, it says "substitute the path to steam executables with your path" and i was woundering (because i cant figure it out by myself) which part are they talking about.

btw my steam install path is /home/wine/drive_c/Program_Files/Steam

---

### Post by minden on 2006-06-29
i dont know if this would work but...
try changing it in windows then run it in wine

---

### Post by underworld288 on 2006-06-29
please explain more.

---

