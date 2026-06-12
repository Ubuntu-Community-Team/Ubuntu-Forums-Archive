---
title: "Which updates to install"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by grandsatrap on 2007-03-12
I'm switching from Windows 98SE to Ubuntu 6 LTS (still running dual boot though).
Question: With Microsoft, if you install all of the operating system upgrades and patches, the Windows directory becomes huge, and chances are that many of the patches will break other things.  With Ubuntu, how do I know which patches to install? How do I distinguish between important security updates and "bloatware" that merely adds more features that I don't need.

Sincere thanks.

---

### Post by impediment on 2007-03-12
TKS 4 this post Grandstrap.  I have been wondering the same thing!  And if you don't install an update will it  come back in future updates?  And if it doesn't, how do U know how to get it if U need the "deleted update" in the future?

---

### Post by oilchangeguy on 2007-03-12
well since microsoft no longer supports 98, you've not had to worry about that problem since 6-06. i've been running xp pro & home for years and never encountered an update that damaged the computer. this computer has been running ubuntu 6.06 for several months now, also no problems with updates. as with microsofts updates you have the option to review them and uncheck those that you don't want.

---

### Post by Kateikyoushi on 2007-03-12
Updates maximum take up some space, but becase few new packages are introduced and updated packages are replaced your system won't really grow neither bog down. 
I upgraded the system 2 times and tested 2 beta version so wen't through a lot of package updates and my system is still running fine.
I am adding all the updates to the system and it is a quite small notebook.

The only updates what you may have to worry about because it could break something will be held back, and have to dist-upgrade to install them.
Be careful with kernel upgrades if you use ati or nvidia drivers.

---

### Post by grandsatrap on 2007-03-12
Oilchangeguy, this still doesn't answer my question. (I'd be leery of automatically installing any updates from Microsoft without examining them -regardless of which Windows version.)

Is the "official best policy" just to install them all?

---

### Post by oilchangeguy on 2007-03-12
it's real simple, read the discription of the update before you decide to install it.

---

### Post by Bachstelze on 2007-03-12
Yes. It will take very little extra diskspace as the new packages will replace the old ones.

---

### Post by Kateikyoushi on 2007-03-12
You could always take these steps to cean up the system from orphaned and old packages. [LINK]("http://ubuntuforums.org/showthread.php?t=140920")

---

### Post by [S|G] on 2007-03-12
On Ubuntu you get patches that are avaliable for every program that you are using and that you installed using the system installer (apt). Usually there are a lot of updates every week, sometimes even every day. 

Unlike windows, however, you'll also be receiving patches for individual pieces of software that are installed, like OpenOffice, the desktop environment and even some games. Usually those patches fix both security issues and also bring new features; that really depends on what the teams responsible for the development of the program release.

Normally you shouldn't worry about "bloatware", though. If you have a program that you don't use, uninstall it (you can uninstall almost anything on the system as long as you know what you're doing; you'll get used to that in time) and you won't receive its updates again.

If you see that you're running low on disk space, it's probably because Ubuntu will save the updates on disk in case you need to install them again; to free up this space, you can type "sudo apt-get clean all".

---

