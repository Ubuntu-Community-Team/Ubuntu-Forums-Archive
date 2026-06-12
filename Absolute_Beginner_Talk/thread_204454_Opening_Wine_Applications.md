---
title: "Opening Wine Applications"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by Danyl on 2006-06-27
Hi all

Need some help opening Windows apps in Wine.

Where does Wine create the c: folder? I want to be able to double click on the .exe files but can't find the folder where I've installed them!

I know they exist cause when I run winecfg, it shows the C: drive and the program file icons but not in Nautlius. 

Where are they?

---

### Post by Xell on 2006-06-27
If you check the properties of C: in winecfg it will tell you were it is mounted. Usually in your home.

---

### Post by dtfinch on 2006-06-27
Press ctrl-h in nautilus to see the hidden files and directories. It'll be in .wine/drive_c under your home directory. The locations of all your drives in wine are determined by the symbolic links in .wine/dosdevices.

---

