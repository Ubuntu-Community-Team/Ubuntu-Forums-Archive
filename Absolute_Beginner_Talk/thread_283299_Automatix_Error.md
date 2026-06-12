---
title: "Automatix Error"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by Sarah13 on 2006-10-24
I am trying to install/run/use Automatix2. I seem to to be getting an error that tells me in order to fix the error I should update, but when I run the update I get the error.

Here's what I ran, from the beginning.

```
penguin@penguin:~$ sudo gedit /etc/apt/sources.list
Password:
penguin@penguin:~$ wget http://www.getautomatix.com/apt/key.gpg.asc
--22:13:29--  http://www.getautomatix.com/apt/key.gpg.asc
           => `key.gpg.asc.2'
Resolving www.getautomatix.com... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730         --.--K/s

22:13:30 (34.37 MB/s) - `key.gpg.asc.2' saved [1730/1730]

penguin@penguin:~$  gpg --import key.gpg.asc
gpg: key 521A9C7C: "Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
penguin@penguin:~$  gpg --export --armor 521A9C7C | sudo apt-key add -
OK
penguin@penguin:~$ sudo apt-get update
Get:1 http://www.getautomatix.com dapper Release.gpg [189B]
Get:2 http://www.getautomatix.com dapper Release [5161B]
Get:3 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:5 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Get:6 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:7 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:8 http://us.archive.ubuntu.com dapper Release [34.8kB]
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.canonical.com dapper-commercial Release
Get:9 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://archive.ubuntu.com dapper Release
Get:10 http://www.getautomatix.com dapper/main Packages [619B]
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://archive.ubuntu.com dapper/main Packages
Get:11 http://packages.freecontrib.org dapper Release.gpg [189B]
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://packages.freecontrib.org dapper Release
Err http://packages.freecontrib.org dapper Release

Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Get:12 http://packages.freecontrib.org dapper Release [9452B]
Get:13 http://us.archive.ubuntu.com dapper/main Packages [619kB]
Ign http://packages.freecontrib.org dapper Release
Hit http://packages.freecontrib.org dapper/free Packages
Hit http://packages.freecontrib.org dapper/non-free Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Get:14 http://archive.ubuntu.com dapper-updates/restricted Sources [14B]
Hit http://archive.ubuntu.com dapper-backports/main Sources
Get:15 http://archive.ubuntu.com dapper-backports/restricted Sources [14B]
Hit http://archive.ubuntu.com dapper-backports/universe Sources
Hit http://archive.ubuntu.com dapper-backports/multiverse Sources
66% [13 Packages 355953/619kB 57%]
Fetched 670kB in 2m16s (4920B/s)
Reading package lists... Done
W: GPG error: http://packages.freecontrib.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems
penguin@penguin:~$

```

I then tried to run the update again, only to receive the same error.

```
penguin@penguin:~$ sudo apt-get update
Get:1 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://www.getautomatix.com dapper Release.gpg [189B]
Hit http://us.archive.ubuntu.com dapper Release
Hit http://www.getautomatix.com dapper Release
Get:3 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:4 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Get:5 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:6 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:7 http://packages.freecontrib.org dapper Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.canonical.com dapper-commercial Release
Get:8 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://archive.ubuntu.com dapper Release
Hit http://packages.freecontrib.org dapper Release
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://www.getautomatix.com dapper/main Packages
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-backports Release
Err http://packages.freecontrib.org dapper Release

Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://archive.ubuntu.com dapper/main Packages
Get:9 http://packages.freecontrib.org dapper Release [9452B]
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/main Sources
Hit http://archive.ubuntu.com dapper-backports/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/universe Sources
Ign http://packages.freecontrib.org dapper Release
Hit http://packages.freecontrib.org dapper/free Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Sources
Hit http://packages.freecontrib.org dapper/non-free Packages
Fetched 9648B in 2s (4705B/s)
Reading package lists... Done
W: GPG error: http://packages.freecontrib.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems
penguin@penguin:~$


```

Can anyone tell me how to fix this?

---

### Post by Sarah13 on 2006-10-24
I've got it! Problem is fixed.

---

### Post by r4ik on 2006-10-24
Solved way to go !

---

### Post by Mimsy on 2006-10-24
I just got a similar error. Would you mind telling me how you solved it?

Thanks,
Mimsy

---

### Post by STREETURCHINE on 2006-10-24
i also have an error but i installed automatix2 and when i tried to run it it told me this version was only for edgy

---

### Post by Mimsy on 2006-10-24
That suggests a relatively easy solution though... uninstall and install the correct version. Done! :)

/Mimsy

---

### Post by Sarah13 on 2006-10-26
> **Mimsy said:**
> I just got a similar error. Would you mind telling me how you solved it?

Thanks,
Mimsy

Not a problem. What happened is that first I had EasyUbuntu, and received the same error, but it also told me to fix the broken packages. So I uninstalled EasyUbuntu, and uninstalled the broken package. Then I added ```
deb http://www.getautomatix.com/apt dapper main
``` to the sources list by entering the sources by ```
sudo gedit /etc/apt/sources.list
```.

I think that this error occurs when either you don't enter the sources list and change it, or when you don't add this into terminal after you edit the sources list.

```
wget http://www.getautomatix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
```

Then hit return to export it and proceed with update and installation!

I hope that fixes it for you!

---

### Post by Mimsy on 2006-10-26
That fixed it; thanks! :)

/Mimsy

---

