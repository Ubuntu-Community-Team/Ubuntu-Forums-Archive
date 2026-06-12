---
title: "Automatix"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by meteora184 on 2006-11-25
i'm using napper, and i tried using the terminal to install automatix, beings that it basically has everything i want right now.

this is what i did to install it :

```
jake@jake-desktop:~$  echo "deb http://www.getautomatix.com/apt dapper main" | sudo tee -a /etc/apt/sources.list
deb http://www.getautomatix.com/apt dapper main
jake@jake-desktop:~$  wget http://www.getautomatix.com/apt/key.gpg.asc
--22:46:00--  http://www.getautomatix.com/apt/key.gpg.asc
           => `key.gpg.asc.3'
Resolving www.getautomatix.com... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730         --.--K/s

22:46:00 (27.05 MB/s) - `key.gpg.asc.3' saved [1730/1730]

jake@jake-desktop:~$ gpg --import key.gpg.asc
gpg: key 521A9C7C: "Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
jake@jake-desktop:~$ gpg --export --armor 521A9C7C | sudo apt-key add -
OK
jake@jake-desktop:~$ sudo apt-get update
Get:1 http://www.getautomatix.com dapper Release.gpg [189B]
Hit http://www.getautomatix.com dapper Release
Get:2 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Get:3 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://www.getautomatix.com dapper/main Packages
Get:4 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:5 http://us.archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://www.getautomatix.com dapper/main Packages
Hit http://archive.ubuntu.com dapper Release
Hit http://us.archive.ubuntu.com dapper Release
Hit http://us.archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Hit http://us.archive.ubuntu.com dapper-updates/restricted Sources
Fetched 5B in 1s (3B/s)
Reading package lists... Done
jake@jake-desktop:~$ sudo apt-get install automatix2
Reading package lists... Done
Building dependency tree... Done
automatix2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
it says that automatix2 is already the newest version, i accidentally installed the .deb for automatix in edgy.

so i'm pretty sure that that means i have to somehow uninstall the bad automatix2, in order to get the better one.

if this is true, could anyone tell me how?  or if this issn't true, then why wouldn't i be able to get automatix?

---

### Post by Shay Stephens on 2006-11-25
Have you tried uninstalling it using the synaptic package manager?  Just open it up, "system - administration - synaptic package manager", and do a search for automatix.  It should show up in the list.  Just right click on it and choose the complete removal option...assuming that napper is anything close in its operation as dapper is ;)

---

### Post by randomi on 2006-11-25
I may be wrong but isn't automatix2 only for Edgy?

Try doing 

```

sudo apt-get install automatix

```

or if that doesn't work

```

sudo apt-get search automatix

```

and see what packages show up and then install the automatix that does.

---

### Post by arnieboy on 2006-11-26
```
sudo apt-get remove automatix2
sudo apt-get update
sudo apt-get clean
sudo apt-get install automatix2
```

---

### Post by Shay Stephens on 2006-11-26
Do what arnieboy posted...he knows what he is talking about ;)

---

### Post by meteora184 on 2006-11-26
k well it worked perfectly, but i got impatient with downloading the fonts and force cancelled it.  (stupid, i know)  but now whenever i try and install something or downlaod it, it says this:
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

whenever i try and manually rune dpkg --configure 
it says :
dpkg: requested operation requires superuser privilege

so how could i fix this?

s

---

### Post by taurus on 2006-11-26
```
sudo dpkg --configure -a
```

---

