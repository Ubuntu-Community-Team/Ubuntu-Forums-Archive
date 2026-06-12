---
title: "newbie need help with wine"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by dj_p03t on 2007-09-01
here is my instalation of and attempted help use of wine first time user and cant figure it out plz help





dustin@dustin-laptop:~$ wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
Password:
OK
dustin@dustin-laptop:~$ sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list
--23:43:00--  [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list)
           => `/etc/apt/sources.list.d/winehq.list'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 181 [text/plain]

100%[====================================>] 181           --.--K/s             

23:43:00 (8.58 MB/s) - `/etc/apt/sources.list.d/winehq.list' saved [181/181]

dustin@dustin-laptop:~$ wine help
The program 'wine' is currently not installed.  You can install it by typing:
sudo apt-get install wine
Make sure you have the 'universe' component enabled
bash: wine: command not found
dustin@dustin-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libartsc0
Suggested packages:
  msttcorefonts xdg-utils
The following NEW packages will be installed:
  libartsc0 wine
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 9821kB of archives.
After unpacking 45.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libartsc0 1.5.6-0ubuntu1 [14.8kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe wine 0.9.33-0ubuntu1 [9807kB]
Fetched 9821kB in 55s (177kB/s)                                                
Selecting previously deselected package libartsc0.
(Reading database ... 105106 files and directories currently installed.)
Unpacking libartsc0 (from .../libartsc0_1.5.6-0ubuntu1_i386.deb) ...
Selecting previously deselected package wine.
Unpacking wine (from .../wine_0.9.33-0ubuntu1_i386.deb) ...
Setting up libartsc0 (1.5.6-0ubuntu1) ...

Setting up wine (0.9.33-0ubuntu1) ...

dustin@dustin-laptop:~$ wine help
wine: creating configuration directory '/home/dustin/.wine'...
wine: '/home/dustin/.wine' created successfully.
wine: could not load L"c:\\windows\\system32\\help.exe": Module not found
dustin@dustin-laptop:~$ wine ?
wine: could not load L"c:\\windows\\system32\\?.exe": Module not found
dustin@dustin-laptop:~$

---

### Post by diatribe on 2007-09-01
the proper input is "wine executable.exe"

---

### Post by dj_p03t on 2007-09-01
> **diatribe said:**
> the proper input is "wine executable.exe"

executable being the program im trying to open with wine?

---

### Post by diatribe on 2007-09-01
indeed, if I wanted to run minesweeper.exe, it would be wine minesweeper.exe in whatever directory minesweeper.exe resides in

---

