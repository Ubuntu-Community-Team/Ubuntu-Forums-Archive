---
title: "Ubuntu 7.04 Sound Problem"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by tenggilingtanah on 2007-07-05
Suddenly, when i try to access file from my mmc card.. my machine was unable to sound me. May be the mmc card having some viruses.. what should i do..

---

### Post by moredhel on 2007-07-05
I promise you it won't be a virus, what it is hoever I don't know, sorry :(

---

### Post by AlexenderReez on 2007-07-05
> **tenggilingtanah said:**
> Suddenly, when i try to access file from my mmc card.. my machine was unable to sound me. May be the mmc card having some viruses.. what should i do..

i had experienced before having virus in mmc card ......after moving file from other computer that use windows ....i remove with antivirus ....avg for linux...but at that time all files already corrupted ..so i just format it....

---

### Post by BobLand on 2007-07-05
Did sound every work for you at all?  If so then check your /etc/modules
```
cat /etc/modules
```

Is your driver there?  Does the list show other drivers?
If so then try this, otherwise skip to the next code section

Backup /etc/modules
```
sudo cp /etc/modules /etc/modules.<today's date>
sudo gedit /etc/modules
```

Delete all of the drivers except yours. 
If your driver is not there then add it.  
It should be the only driver listed.

Save the file
```
Ctrl-s
```

Quit editing
```
Ctrl-q
```


Now run
```
sudo apt-get update && sudo aptitude dist-upgrade
reboot
```

Still no sound?
run this sequence
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
sudo apt-get update && sudo aptitude dist-upgrade
reboot
```

If you find this sequence to work then make a note of it or bookmark it.  More then likely installing an update/upgrade or new program might break your sound again.  Running the above code will fix it.

Hope this helps,
bobland

---

