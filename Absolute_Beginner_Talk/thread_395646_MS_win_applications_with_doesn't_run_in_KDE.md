---
title: "MS win applications with doesn't run in KDE"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by g1psas on 2007-03-28
I have installed Kubuntu desktop on my Ubuntu 6.10 edge. Now some windows programs (mIRC, Counter strike) don't run through wine on KDE. In gnome everything is   OK.

---

### Post by ArieT on 2007-03-28
Strange ... haven't you got some error messages? Why have you install mirc while there is Xchat for gnome and lots of other clients for KDE?

---

### Post by g1psas on 2007-03-28
No, I duoble-click the application and nothing happens. I spend most time on winXP and mIRC is best for me. There weren't such problems in GNOME :(

---

### Post by igknighted on 2007-03-28
try starting them through the terminal (wine application.exe I believe).  It should give you error messages as to why it fails.

---

### Post by g1psas on 2007-03-28
In wine config I added applicantion, but:
"wine: could not load L"c:\\windows\\system32\\mirc.exe": Module not found"
it also can't find directory \media\d\... where I installed mirc.

---

### Post by muguwmp67 on 2007-03-28
It sounds like kubuntu-desktop could have broken a dependency.  I don't know how you installed wine the first time, but if its coming from a repository, reinstalling it might help.

In synaptic, you reinstall by right-clicking the package and selecting 'mark for reinstallation'.

I don't know how to generate a debug log in wine, but that would probably help you track down the issue if reinstalling doesn't fix it.  In cedega (a branch of wine) there's an option for it in the File menu.

edit:
<just saw the last post>
Nevermind.

Did you check to see if your drives are mounted in KDE, with the same paths?

---

### Post by g1psas on 2007-03-28
I tried to reinstall wine, but I also can't open windows applicantions. Yes, the same drives paths.

---

### Post by Quintin Riis on 2007-03-28
mIRC is crap.  

Look at the WINE appdb for WINE issues.

---

### Post by muguwmp67 on 2007-03-28
> **g1psas said:**
> I tried to reinstall wine, but I also can't open windows applicantions. Yes, the same drives paths.

Do you mean you can't open applications after rebooting to windows?  (I hope not)

Can you locate the executable again and reset the path in wine?

---

### Post by plainjane on 2007-03-28
Actually, I have problems in Wine in Kde too.  My DVD Shrink and DVD Decryptor will not recognize my dvd drive in Kde but work great in Gnome.  Strange. I just stick with Gnome now.   Hope you can get yours to work!

---

### Post by g1psas on 2007-03-29
No, in windows everything runs great. The main problem is that wine does't run any WIN program. Now I tried to run program in new window system asked me, execute or not. I pressed execute and no action happened.

---

