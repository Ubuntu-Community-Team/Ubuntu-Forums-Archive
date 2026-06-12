---
title: "Older version of wine"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by jordank on 2008-01-04
If i wanted to install and use an older version of wine (0.9.43) how would i go about doing this?  I have the most recent version installed right now, and i'm running 64bit linux.

Does anyone have a link that i could use to get the 64bit version of 9.43?  Also, how would i go about completely removing the version i have now, and reinstalling with the 9.43 version?

---

### Post by PmDematagoda on 2008-01-04
[Here]("http://wine.budgetdedicated.com/archive/index.html") is where you can get the older versions of Wine, the AMD64 versions are included.

---

### Post by Rocket2DMn on 2008-01-04
Remove your current version with
```
sudo apt-get remove wine
```
You can download the version you want at [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) and either double click the .deb file or run
```
dpkg -i filename.deb
```
You will have to tell synpatic/apt-get no to update by opening the Synaptic Package Manager, searching for wine, selecting it and going to Package->Lock Version

---

### Post by stump138 on 2008-01-04
You can download a .deb package for the version you want [here]("http://wine.budgetdedicated.com/archive/index.html")

Remove your old version of wine
```
sudo apt-get remove wine
```

then install the .deb package.  You can ignore the warning that there is a newer version and you should be all set.  Your package updater will want to update, so if you want you can lock the version in synaptic to make the update prompt go away.

---

### Post by stump138 on 2008-01-04
lol I type to slow :P

---

### Post by jordank on 2008-01-04
after typing 
sudo apt-get remove wine

the "wine" menu is still left in my applications dropdown menu, and it still has applications in it.

How do i COMPLETELY remove wine?

---

### Post by PmDematagoda on 2008-01-04
```
sudo apt-get purge wine
```
should do the trick.

---

### Post by jordank on 2008-01-04
it still left the 
.wine
folder in my home folder.

Would manually deleting this folder remove everything about wine?
after typing sudo apt-get remove wine

---

### Post by jordank on 2008-01-04
jordan@Jorcomp:~$ sudo apt-get purge wine
[sudo] password for jordan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
The following packages were automatically installed and are no longer required:
  liblzo1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jordan@Jorcomp:~$

---

### Post by PmDematagoda on 2008-01-04
I don't think it is really necessary to delete the .wine folder when upgrading or downgrading Wine.

---

### Post by Thunar on 2008-01-04
Check your other post at [http://ubuntuforums.org/showthread.php?t=658277](http://ubuntuforums.org/showthread.php?t=658277), I might have a solution to your Warcraft 3 problem. I really think your Wine version isn't the problem, but rather your "Windows" version. 

Also you may want to check out WineHQ at [http://www.winehq.org/](http://www.winehq.org/) to see if there is a maintainer for that program, if so they'll help you get it up and running.

good luck.

---

