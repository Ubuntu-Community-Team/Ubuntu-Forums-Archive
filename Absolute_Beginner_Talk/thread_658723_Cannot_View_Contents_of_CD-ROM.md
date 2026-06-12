---
title: "Cannot View Contents of CD-ROM"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by ExBuM on 2008-01-04
I'm trying to install Lord of the Rings: Return of the King using WINE. However I can't access setup.exe in the first installation disk. When I put in the CD I get this message:
"You do not have the permissions necessary to view the contents of 'cdrom0'."

When I mount it from the terminal with sudo it tells me that the CD is write-protected. So How do I get this game working?

---

### Post by toddward on 2008-01-05
It being write protected is a normal thing.  I'd suggest trying to copy off the .exe somewhere and executing it from there.

---

### Post by ExBuM on 2008-01-05
Oh yeah I forgot to mention what when I use sudo nautilus I can view the files. However I cannot copy them for some reason.

---

### Post by ryanVickers on 2008-01-05
you probably need to configure wine to allow the CD drive ... go Applications > Wine > and click Configure Wine.  Go to the "Drives" tab, and click "auto-detect".  Then, make sure there is an entry for /media/cdrom (also, if you feel comfortable, just enter this yourself and skip the auto-scan)

---

### Post by ExBuM on 2008-01-05
I got the installer to run and it's saying "Cannot find required DLL 'H:\AutoRunGUI.DLL'" (I tried Setup.exe but nothing happened). H:\ is my /home/user folder. I tried copying but the CD won't let me copy anything >_>
Why is the installer looking in the home folder?

---

### Post by harvodan on 2008-02-20
If anyone's still watching this thread...you need to open a terminal, which is best done by navigating to the folder in Nautilus, then right-click and select open terminal from the menu. Then type wine setup.exe, that'll get it working.

---

