---
title: "Ubuntu desktop question..."
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by JasonNewb on 2006-06-23
When I install ubuntu desktop, do I get to choose between Gnome, KDE or X?

Thanks

---

### Post by oscar on 2006-06-23
The ubuntu-desktop package (the default ubuntu desktop package) installs gnome. If you want kde then you have to install kubuntu-desktop. If you want xfce then you have to install xubuntu-desktop. If you have already decided which desktop environment you want then you can download the correct install cd (ubuntu, kubuntu or xubuntu)

---

### Post by Tedd on 2006-06-23
You can install either/all of them through Synaptic or Aptitude, and then switch at your sessions login.

---

### Post by wpshooter on 2006-06-23
[QUOTE=JasonNewb]When I install ubuntu desktop, do I get to choose between Gnome, KDE or X?

Thanks[/QUOTE]

Make sure you look at each of them first before deciding on one.

Make sure you look at and are comfortable with the default applications installed with each different GUI.  Personally, I prefer Gnome with Open Office, Evolution and Firefox combination.

Good luck.

---

### Post by aysiu on 2006-06-23
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html) explains the process.

---

### Post by JasonNewb on 2006-06-23
Ok, so I have to download xubuntu and create the CD then I can install X?  I'm just running a server install so I dont need much.

---

### Post by aysiu on 2006-06-23
Do you have an internet connection? Because if you do, you don't need to download and create a CD, you can (from your server install) just type ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by JasonNewb on 2006-06-23
Yep, the internet connection works fine.  Thanks, I'll give that a shot.

---

### Post by bohboh on 2006-06-23
For anyone else, here are guides i followed and worked ok.

[http://ubuntuguide.org/wiki/Dapper#Other_Desktop_Environments]("http://ubuntuguide.org/wiki/Dapper#Other_Desktop_Environments")

---

### Post by aysiu on 2006-06-23
[QUOTE=bohboh]For anyone else, here are guides i followed and worked ok.

[http://ubuntuguide.org/wiki/Dapper#Other_Desktop_Environments]("http://ubuntuguide.org/wiki/Dapper#Other_Desktop_Environments")[/QUOTE]
While that will appear to work, I would strongly recommend against installing desktop environments with *apt-get*.

Read more here:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by bohboh on 2006-06-23
I just this minute used aptitude to uninstall gdesklets:

```

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are BROKEN:
  gdesklets-data
The following packages are unused and will be REMOVED:
  libdbd-mysql-perl **mysql-client-5.0 mysql-server-5.0**
The following packages have been kept back:
  mozilla-browser xserver-xorg-driver-ati
The following packages will be REMOVED:
  gdesklets
0 packages upgraded, 0 newly installed, 4 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 66.2MB will be freed.
The following packages have unmet dependencies:
  gdesklets-data: Depends: gdesklets (>= 0.35) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gdesklets [0.35.3-1ubuntu3 (dapper, now)]

```

Was it about to uninstall the packages in bold? Being a web developer i would definately not want this to remove my db server. How did it decide that it was unused? It has databases and is running, and is in use.

---

