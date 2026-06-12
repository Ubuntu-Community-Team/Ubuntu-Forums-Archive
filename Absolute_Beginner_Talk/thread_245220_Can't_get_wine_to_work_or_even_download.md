---
title: "Can't get wine to work or even download"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by dchglat on 2006-08-27
Alright first off I'm completely new to ubuntu and linux.I have tried searching for an answer throughout these forums but can't find anything, so I apologize if this has already been answered.

I am trying to install wine. I have tried following the instructions on wineHQ and on these forums that say add "deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main" to the repository list but it returns the message 'Could not update repository lists' and "http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz: 404 Not Found"

I'm running on an amd athlon 64 3300 and have the 64 bit version of ubuntu installed. I figured maybe this was the problem since (from what I gather) wine is only available in 32 bit version. But I stumbled upon this [http://www.ubuntuforums.org/showthread.php?t=185557&highlight=trouble+wine]("http://www.ubuntuforums.org/showthread.php?t=185557&highlight=trouble+wine")
I ran the script and it installed 3 packages but couldn't download wine. The same message as before came wine.budgetdedicated.com...etc... 404 file not found. What's wrong? Is it me or does anyone else have this problem?

Thanks for any advice.

---

### Post by dchglat on 2006-08-29
I have now tried following the how to ([http://www.ubuntuforums.org/showthread.php?t=185557&highlight=trouble+wine](http://www.ubuntuforums.org/showthread.php?t=185557&highlight=trouble+wine))  by myself at but get stuck at the command "sudo dpkg --force-architecture -i wine_0.9.19~winehq1~ubuntu~6.06-2_i386.deb" and it fails to continue.

---

### Post by Druidor on 2006-08-29
You can get teh latest version of Wine here (0.9.20)

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

once downloaded you should be able to just double click to install the .deb package.

once installed you need to open the terminal & type *winecfg* to set it up.

---

### Post by x140l31 on 2006-08-30
I think that the problem is that the architecture is "i386" because when I download the .deb package it says that have an error with the architecture.

I'm a complete newby if I'm wrong sorry xDDD I'm trying to learn more of this theme.:-k

---

### Post by dchglat on 2006-08-30
> **Druidor said:**
> You can get teh latest version of Wine here (0.9.20)

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

once downloaded you should be able to just double click to install the .deb package.

once installed you need to open the terminal & type *winecfg* to set it up.


Wait. So, just install the version for a pentium and it'll work right?

---

### Post by Kilz on 2006-08-30
The solution to Wine on 64bit Ubuntu is in my signature. [The howto can also be found here.]("https://help.ubuntu.com/community/WineForAMD64") If you cant follow the howto there is a automated setup script on either page.
If you are having problems with a 64bit install [I recommend posting to the 64bit section.]("http://www.ubuntuforums.org/forumdisplay.php?f=134")

---

### Post by Jareth on 2006-08-30
Hi,
a newbie myself, but I was having a look in the add/remove programs thing and I found wine there.
I haven't had a good go on it yet, so not sure if that works, but it says its there.

Hope thats useful,
I'll give it a try later and see whats what.

---

### Post by Kilz on 2006-08-30
> **Jareth said:**
> Hi,
a newbie myself, but I was having a look in the add/remove programs thing and I found wine there.
I haven't had a good go on it yet, so not sure if that works, but it says its there.

Hope thats useful,
I'll give it a try later and see whats what.

The problem is that hes running a 64bit version of Ubuntu. You need to do some additional setup with that version for wine.

---

### Post by dchglat on 2006-09-07
thank you kilz

---

