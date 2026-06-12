---
title: "trouble installing ubuntu studio (to existing feisty installation)x2"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by thelegionnaire on 2007-06-28
ok so i added the deb to my sources.list, then followed the other steps heres the copy and paste from the ol' terminal:

m@m-laptop:~$ sudo su -c ’echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list’
bash: /etc/apt/sources.list’: Permission denied
m@m-laptop:~$ sudo su -c ’echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list’
bash: /etc/apt/sources.list’: Permission denied
m@m-laptop:~$ sudo gedit /etc/apt/sources.list
Password:
m@m-laptop:~$ wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update
OK
Get:1 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release.gpg [189B]
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_CA
Get:2 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release [1304B]
Get:3 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_CA
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release
Get:4 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_CA
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release
Get:5 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_CA
Get:6 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty Release.gpg [191B]
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty/main Translation-en_CA
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_CA
Get:8 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_CA
Ign [http://deb.zeitherrschaft.org](http://deb.zeitherrschaft.org) binary/ Release.gpg
Ign [http://deb.zeitherrschaft.org](http://deb.zeitherrschaft.org) binary/ Translation-en_CA
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_CA
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_CA
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_CA
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release
Ign [http://deb.zeitherrschaft.org](http://deb.zeitherrschaft.org) binary/ Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_CA
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_CA
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty/main Packages
Ign [http://deb.zeitherrschaft.org](http://deb.zeitherrschaft.org) binary/ Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_CA
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty/main Packages
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources
Hit [http://deb.zeitherrschaft.org](http://deb.zeitherrschaft.org) binary/ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Fetched 1502B in 2s (534B/s)
Failed to fetch [http://archive.ubuntustudio.org/ubun...feisty/Release](http://archive.ubuntustudio.org/ubun...feisty/Release) Unable to find expected entry main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
m@m-laptop:~$ sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-desktop ubuntustudio-graphics ubuntustudio-video
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntustudio-desktop
m@m-laptop:~$ 

any help would be appreciated

---

### Post by Seisen on 2007-06-28
I think they are having problems with their repo. I tried opening it up and it gave me a 404 error.

---

### Post by cogadh on 2007-06-28
> **thelegionnaire said:**
> ok so i added the deb to my sources.list, then followed the other steps heres the copy and paste from the ol' terminal:

m@m-laptop:~$ sudo su -c ’echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list’
bash: /etc/apt/sources.list’: Permission denied
m@m-laptop:~$ sudo su -c ’echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list’
bash: /etc/apt/sources.list’: Permission denied


I think part of the problem my be the **’** character you used, it should be **'** (single quote)

---

### Post by LancerDragoon on 2007-06-28
Are you using a 64-bit system? There are currently no UbuntuStudio 64-bit packages, unfortunately.

---

### Post by Seisen on 2007-06-28
I tried opening up the Ubuntu studio repo through firefox and it wouldn't come up.

---

### Post by LancerDragoon on 2007-06-28
> **Seisen said:**
> I tried opening up the Ubuntu studio repo through firefox and it wouldn't come up.

Could be that too. I can't open it up either.

---

### Post by thelegionnaire on 2007-06-28
yes i am 64-bit, are there any plans on an uupdate for that? also, is there anyway i could just get ardour without compiling from source?

---

