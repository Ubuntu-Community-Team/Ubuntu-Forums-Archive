---
title: "deb question"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-08
I downloaded wine-9.22 and have the deb sitting in my temp drive. How do I launch it so I can start using wine?

---

### Post by Madpilot on 2006-10-08
Double-click on the .deb file to install it.

---

### Post by gila_monster on 2006-10-08
Or, from the command line, you can try

dpkg -i <name of deb>

---

### Post by 3rdalbum on 2006-10-09
Wine actually has its own repository for Debian and Ubuntu, so you don't need to manually check for new versions, then manually download and install Wine.

```
gksudo gedit /etc/apt/sources.list
```

Add the following line to the bottom of the file:

```
deb http://wine.budgetdedicated.com/apt dapper main
```

Save your changes and quit Gedit. Go into Synaptic and Reload Package Information, then search for Wine and install it. If you have it set to automatically check for updates, you'll be notified when a new Wine is available.

---

### Post by saintj0n on 2006-10-09
uh oh..I see something different than what I typed. I punched in sudo -s vi /etc/apt/sources.list

I also tried going to synaptic and changing the repository manually. It didn't work so I downloaded the deb. I did try clicking on it and it didn't work:(

---

### Post by saintj0n on 2006-10-09
ok..tried the gksudo gedit thing and I think it worked but it gave me:

jonathan@jonathan-laptop:~$ gksudo gedit /etc/apt/sources.list
(gedit:14286): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by distroman on 2006-10-09
You don't need to worry about that error message, it has to do with “Running Sudo Graphically”
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

If you have not used wine before, you might want to have a look at the following, to ease working with wine.
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
[http://www.ubuntuforums.org/showthread.php?t=149585&highlight=WINE](http://www.ubuntuforums.org/showthread.php?t=149585&highlight=WINE)

---

### Post by snakyjake on 2006-10-09
> **saintj0n said:**
> I downloaded wine-9.22 and have the deb sitting in my temp drive. How do I launch it so I can start using wine?

[https://help.ubuntu.com/ubuntu/desktopguide/C/install-file.html#install-deb](https://help.ubuntu.com/ubuntu/desktopguide/C/install-file.html#install-deb)

---

