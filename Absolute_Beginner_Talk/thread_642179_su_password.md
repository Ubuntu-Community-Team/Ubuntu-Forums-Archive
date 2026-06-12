---
title: "su password"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by in2media on 2007-12-16
trying to run a command in konsole but says i need administrator priviliges
so i type in su then my password and it says failure

---

### Post by overdrank on 2007-12-16
> **in2media said:**
> trying to run a command in konsole but says i need administrator priviliges
so i type in su then my password and it says failure

Hi and maybe this link will help
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Pumalite on 2007-12-16
'sudo' in Ubuntu.

---

### Post by in2media on 2007-12-16
heres my problem!
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
now when i try run the command it says to run i get this
john@john-desktop:~$ sudo dpkg --configure -a
Password:
dpkg: parse error, in file `/var/lib/dpkg/updates/0030' near line 1:
 field name `' must be followed by colon
john@john-desktop:~$ sudo 'dpkg --configure -a'
sudo: dpkg --configure -a: command not found
john@john-desktop:~$


all help appreciated guys

---

### Post by Pumalite on 2007-12-16
Post output of:
sudo apt-get install -f

---

### Post by in2media on 2007-12-16
john@john-desktop:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
john@john-desktop:~$

---

### Post by Pumalite on 2007-12-16
Output of:
sudo apt-get update

---

### Post by in2media on 2007-12-16
sudo apt-get update

---

### Post by in2media on 2007-12-16
john@john-desktop:~$ sudo apt-get update
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB
Get: 2 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_GB
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_GB
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Sources
Fetched 192B in 0s (205B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
john@john-desktop:~$

---

### Post by in2media on 2007-12-16
would it be best just to do a re-install and start again

---

### Post by Pumalite on 2007-12-16
Probably.

---

### Post by warrior24 on 2007-12-16
I had the same problem in Debian but it was my fault an update was taking to long so i shut down my box. But I ended up installing ubuntu so its all good, I hope you outcome is better:):):)

---

### Post by seventhc on 2007-12-16
You can su in ubuntu but you need to set the password under System>Administration>Users and Groups and reset roots password, then if you want to su in you can. But sudo is good enough I'm just pointing out that you can su in as root.

---

### Post by bhold on 2007-12-16
I don't have any files on my system under /var/lib/dpkg/updates/. So maybe there is something corrupted in that directory from the earlier dpkg problem. You might try removing the contents of that directory and trying dpkg again. You can copy the contents of /var/lib/dpkg/updates/ to /tmp before removing the files just in case there might be something you need there.

---

### Post by asmoore82 on 2007-12-16
> **in2media said:**
> heres my problem!
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
now when i try run the command it says to run i get this
john@john-desktop:~$ sudo dpkg --configure -a
Password:
dpkg: parse error, in file `/var/lib/dpkg/updates/0030' near line 1:
 field name `' must be followed by colon
john@john-desktop:~$ sudo 'dpkg --configure -a'
sudo: dpkg --configure -a: command not found
john@john-desktop:~$


all help appreciated guys

no single quotes ...
```
$ sudo dpkg --configure -a
```

---

### Post by Pumalite on 2007-12-16
Right. I missed that.

---

