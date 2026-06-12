---
title: "wers my wine?"
date: 2005-09-09
forum: Absolute Beginner Talk
---

### Post by nikita12 on 2005-09-09
i type this
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo gedit /etc/apt/sources.list &
sudo apt-get update
sudo apt-get install wine

did i get it right? i dont see wer i put my wine in my desktop?

---

### Post by xequence on 2005-09-09
When you click a .exe it will open in wine. Or right click and choose open with, type in wine.

---

### Post by nikita12 on 2005-09-09
athalie@natzvin:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
nathalie@natzvin:~$ sudo gedit /etc/apt/sources.list &
[1] 7614
nathalie@natzvin:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Fetched 4B in 2s (2B/s)
Reading package lists... Done
nathalie@natzvin:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
wine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 51 not upgraded.
nathalie@natzvin:~$



i still dont know wer my wine is i tried to open exe file but there no wine program in my application :(

---

### Post by aysiu on 2005-09-09
[QUOTE=nikita12]
wine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 51 not upgraded.[/quote] This means it's already installed.

> 
i still dont know wer my wine is i tried to open exe file but there no wine program in my application :( Wine doesn't run as an independent application. It tries to launch when you double-click an .exe file. Sometimes it works. Sometimes it doesn't. It depends on the .exe. Try winword.exe if you have it.

Maybe you should read some of the [Wine documentation](http://www.winehq.com/site/documentation) to get a better sense of how the program works.

---

