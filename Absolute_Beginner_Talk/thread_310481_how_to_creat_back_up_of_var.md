---
title: "how to creat back up of /var"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-12-01
i have been sing kubuntu and now i want to remove it and install ubuntu. i don't want to delete my /var because doing this will require me to have a fresh download of all the softwares i have installed. i don't want to do so. i tried copy paste but it does not work. can anybody tell me how to create a backup copy of all debian packages found in  /var

---

### Post by cookfromfrozen on 2006-12-01
Type sudo apt-get install ubuntu-desktop in the terminal.  After it's done, log out and choose Gnome as the session from the button underneath where you type the username.  Once you're logged into Gnome type sudo apt-get remove kubuntu-desktop to remove KDE.

---

### Post by u04f061 on 2006-12-08
> **cookfromfrozen said:**
> Type sudo apt-get install ubuntu-desktop in the terminal.  After it's done, log out and choose Gnome as the session from the button underneath where you type the username.  Once you're logged into Gnome type sudo apt-get remove kubuntu-desktop to remove KDE.

my question was not how to install gnome. my question was how to create a backup copy of debian packages stored in /var directory

---

### Post by brt on 2006-12-08
usually all packages are stored in /var/cache/apt/archives/ so all you have to is copy this directory:

sudo cp -a /var/cache/apt/archives /your/backup/destination

after you have installed ubtuntu you can copy it back:

sudo cp -a /your/backup/destination/archives /var/cache/apt/

and you will not need to download all the software again.

---

### Post by Wim Sturkenboom on 2006-12-08
The commandline option (I don't know another one)
```
tar -cvzf myvar.tar.gz /var
```This will create an archive (kind of zip) in the current directory of **everything** in /var.
To extract
```
cp myvar.tar.gz /
cd /
tar -xvzf myvar.tar.gz
```

To verify that the creation of the archive went OK, you can extract it in your home directory or use the -t option (probably tar -tzf myvar.tar.gz, never tried it).

PS you probably need root permissions to access parts of /var, so use sudo

---

