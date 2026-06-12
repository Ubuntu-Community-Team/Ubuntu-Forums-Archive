---
title: "Dell 1390 wifi card ndiswrapper problem"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by iamthemicrowave on 2007-10-10
Hi. I currently have ~/.driver with the extracted ndiswrapper 1.48 and a wifi folder inside of it.  Inside the wifi folder is my driver R140747.EXE.  I am having problems installing the driver, if I am understanding the problem correctly

$ sudo ndiswrapper -i ~/.driver/wifi/R140747.EXE/bcmwl5.inf
driver bcmwl5 is already installed

$ sudo ndiswrapper -l
bcmwl5 : invalid driver!
r140747.exe : invalid driver!

Why do I get these messages? Please help me.

---

### Post by kevdog on 2007-10-10
You need to open the .exe file and get the .sys and .inf file out of the .exe file. The .exe file is either a self extracting zip file or cabextract file.  I dont know which.  If you have a windows computer, probably the easiest thing would be to open the file there, get the windows xp .sys and .inf files, and then bring these two files back to Ubuntu and install them in ndiswrapper.

---

### Post by iamthemicrowave on 2007-10-10
Ok, i extracted the driver fine.  How do i uninstall the old ndiswrapper 1.42? I deleted its folder before, but it was in my home directory.  Would that fix it?

Now when i try to install ndiswrapper 1.48, i get

$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.

I did this command over and over, but it still occurs. Please help.

---

