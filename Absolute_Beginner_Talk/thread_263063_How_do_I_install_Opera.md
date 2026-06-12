---
title: "How do I install Opera?"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2006-09-22
How do I install Opera 9? I tried in the terminal
```
sudo aptitude update
sudo apt-get install Opera
```

but this came up
```
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate

```
Please help.

---

### Post by SunnyRabbiera on 2006-09-22
you have to do it the normal way, go to opera.com and download opera.
its not in the repository.

---

### Post by Narcoleptic_Insomniac on 2006-09-22
> **SunnyRabbiera said:**
> you have to do it the normal way, go to opera.com and download opera.
its not in the repository.

I did do it the normal way but there was no install thingy in the folder. There was an install.sh but I tried to run it and nothing happened.

---

### Post by Dinerty on 2006-09-22
Try

```
sudo gedit /etc/apt/sources.list
```

then copy:

##The Opera browser
##Opera provides their own packages here
## The Opera browser (packages)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

then save and close it down

```
sudo apt-get update
```

then

```
sudo apt-get install opera
```

OR

goto [http://www.opera.com/download/](http://www.opera.com/download/)

Select distribution to Ubuntu > Dapper Drake 6.06 then click download, this will download the .deb and deal with dependicies

---

### Post by Narcoleptic_Insomniac on 2006-09-22
Naw I got it, thanks for trying guys.

---

### Post by SunnyRabbiera on 2006-09-22
just use the ubuntu .deb file:
first go to opera.com and then under the "select distributer" pulldown menu select ubuntu.
then select the one for your version of ubuntu, dapper, edgy, breezy, etc.
just download the debian package, open the folder you put it in and double click it and you should get it installed soon.

---

### Post by JAwuku on 2006-09-22
Two ways:

You can either add a special repository from Canonical or you can download the .deb package from Opera.

**_1st Method_**

open the repository configuration file:

```
gksudo gedit /etc/apt/sources.list
(if using kubuntu, use kdesu kwrite /etc/apt/sources.list)
```

Add this text to the end of the file, and save it:

```
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

install:

```
sudo apt-get update
sudo apt-get install opera
```

**_2nd Method_**

Download the new Opera 9.02 from the website:

[http://www.opera.com/download/index.dml?opsys=Linux%20i386&lng=en&ver=9.02&platform=Linux%20i386&local=y](http://www.opera.com/download/index.dml?opsys=Linux%20i386&lng=en&ver=9.02&platform=Linux%20i386&local=y)

and install by ```
sudo dpkg -i <name of package>
```

---

### Post by TheRingmaster on 2006-09-22
If I install opera from there website, does opera autoupdate?

I know that if you install it from the respositories you have to wait until that version is uploaded to the servers.

---

### Post by houseisland on 2006-09-22
If you have Opera 9 already installed you have uninstall it to install 9.02.

For me the 9.02 install generated error an message about dependancy conflicts with the earlier 9 version, even though I had already uninstalled it.  The error message seems to be an error itself, though, because Opera 9.02 is now installed and working fine and the system itself reports no conflicts.

:confused:

---

