---
title: "Installing Wine?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-05-12
I use KDE.

I get this...
nic@nic-desktop:~$ wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O-                                                        | sudo apt-key add -
OK
nic@nic-desktop:~$ sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/winehq.list
--16:37:13--  [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list)
           => `/etc/apt/sources.list.d/winehq.list'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 139 [text/plain]

100%[===========================================================================================>] 139           --.--K/s

16:37:13 (13.26 MB/s) - `/etc/apt/sources.list.d/winehq.list' saved [139/139]

nic@nic-desktop:~$ wine /path/to/setup.exe
bash: wine: command not found
nic@nic-desktop:~$ wine /path/to/media/cdrom0/setup.exe
bash: wine: command not found
nic@nic-desktop:~$ wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg)
nic@nic-desktop:~$
nic@nic-desktop:~$ wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
OK
nic@nic-desktop:~$ sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/winehq.list
--16:40:07--  [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list)
           => `/etc/apt/sources.list.d/winehq.list'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 139 [text/plain]

100%[===========================================================================================>] 139           --.--K/s

16:40:08 (14.73 MB/s) - `/etc/apt/sources.list.d/winehq.list' saved [139/139]

nic@nic-desktop:~$

[/code]

What do I do? :( What am I doing wrong?

---

### Post by aardwolfsgp on 2007-05-12
Did u install wine?
sudo apt-get install wine

---

### Post by Enverex on 2007-05-12
Please tell me you weren't really expecting "wine /path/to/setup.exe" to work either? :/

As aard said, you need to actually install Wine, it looks like you just kept trying to install the GPG key for some reason...

---

### Post by LollYouSuckZor on 2007-05-12
nic@nic-desktop:~$ sudo apt-get install wine
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  msttcorefonts
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 713 not upgraded.
Need to get 9853kB of archives.
After unpacking 44.8MB of additional disk space will be used.
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main wine 0.9.36~winehq0~ubuntu~6.10-1
  404 Not Found
Failed to fetch [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.36~winehq0~ubuntu~6.10-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.36~winehq0~ubuntu~6.10-1_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by taurus on 2007-05-12
Can you post your /etc/apt/sources.list?  Looks like you have some dead repos in there.

```
cat /etc/apt/sources.list
```

---

### Post by LollYouSuckZor on 2007-05-12
```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty universe multiverse
deb http://us.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

```


:(

---

### Post by taurus on 2007-05-12
Are you running Feisty or Edgy?  You have Feisty repos but somehow you installed Edgy key for wine.budgetdedicated.com?

---

### Post by Nythain on 2007-05-12
first off, it wont be in his sources.list file because of the way it was added it will be located in /etc/apt/sources.list.d/winehq.list
it should have these two entries
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
if not then just put those at the bottom of your /etc/apt/sources.list
then
sudo apt-get update
sudo apt-get install wine
that should do the trick
you might have to get the right gpg key for the feisty repo instead of the edgy one

---

### Post by LollYouSuckZor on 2007-05-12
> **taurus said:**
> Are you running Feisty or Edgy?  You have Feisty repos but somehow you installed Edgy key for wine.budgetdedicated.com?

Im using KDE.. so I guess edgy..
Someone helped me fix my Sources list, so I guess thats where that came from.

---

### Post by Nythain on 2007-05-12
ok, when you installed (K)Ubuntu did you install version 6.10 edgy eft or or 7.04 feisty fawn???

---

### Post by LollYouSuckZor on 2007-05-12
> **Nythain said:**
> ok, when you installed (K)Ubuntu did you install version 6.10 edgy eft or or 7.04 feisty fawn???
6.10


I think wines installed...
How do I get it to start installing Battlefield 2 :)

---

### Post by LollYouSuckZor on 2007-05-12
=D!

[http://img184.imageshack.us/img184/633/zomgjf6.png](http://img184.imageshack.us/img184/633/zomgjf6.png)

---

### Post by LollYouSuckZor on 2007-05-12
Thanks to those of you who helped me! :D

---

### Post by Enverex on 2007-05-13
Erm, on a side note it looks like you're trying to break your install of Ubuntu. You say you're running Edgy but you've switched all your sources to Feisty...

---

