---
title: "Automatix install problems"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by BigDawg2 on 2006-10-09
Been trying for hours to install this program with no luck. I do not know where to go from here. Any suggestions would be greatly appreciated.

lori@LoriComputer:~$ sudo gedit /etc/apt/deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

(gedit:5110): libgnomevfs-WARNING **: trying to read a non-existing handle
lori@LoriComputer:~$ wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
--09:03:52--  [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
           => `key.gpg.asc.10'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.194.143
Connecting to www.getautomatix.com|82.165.194.143|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730         --.--K/s

09:03:52 (17.37 MB/s) - `key.gpg.asc.10' saved [1730/1730]

lori@LoriComputer:~$ gpg --import key.gpg.asc
gpg: key 521A9C7C: "Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
lori@LoriComputer:~$ gpg --export --armor 521A9C7C | sudo apt-key add -
OK
lori@LoriComputer:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Get:4 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg [189B]
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Get:5 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release [9421B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Fetched 9627B in 2s (4040B/s)
Reading package lists... Done
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems
lori@LoriComputer:~$ sudo apt-get install automatix2
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package automatix2

---

### Post by PPAAUULL on 2006-10-09
Are you sure you have the right key? also you can go into synaptic sources and check that the key is installed right.

---

### Post by Ben Sprinkle on 2006-10-09
What the hell is:
[http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release

And why don't you just use synaptic to get your program?

---

### Post by bluefrog on 2006-10-09
sudo gedit /etc/apt/deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

not a lot of chance to add the repo to your sources.list like that..

sudo gedit /etc/apt/sources.list

and then add deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

close
sudo apt-get update

James

---

### Post by xpod on 2006-10-09
I follow this guide to install automatix...works everytime

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

EDIT..from the "installing with apt"...section

---

### Post by BigDawg2 on 2006-10-09
> **bluefrog said:**
> sudo gedit /etc/apt/deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

not a lot of chance to add the repo to your sources.list like that..

sudo gedit /etc/apt/sources.list

and then add deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

close
sudo apt-get update

James

This is what i needed to fix my problem. This is my second day working with linux so i have a long way to go. Thanks for all your help.

---

### Post by petebbbandt on 2006-10-10
I was about to ask that question as well BigDawg. I have only had Linux a couple of days as well and I was about to pull out what remains of my hair trying to get round this automatix thing. Bluefrog's answer did it for me as well. Pity the install instructions from automatix aren't so clear.

Thanks guys

---

### Post by Chickenfoot on 2006-10-10
This is gong to be the dumbest NooB question EVER. Do you have to have Automatix 1 before you get A2? Or you you just go and get A2?

Blushing Sheepishly:mrgreen:

---

### Post by Medieval_Creations on 2006-10-10
Yea you can get Automatix2 without getting Automatix, just put the 2 at the end of the command.

```
sudo apt-get install automatix2
```
or
```
sudo aptitude install automatix2
```
or

use Synaptic like GS suggested (once you get the sources.list error fixed).


> **Goat Spirit said:**
> What the hell is:
[http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release

I totaly agree with GS on this... I've seen this error come up for this url in quite a few threads & I have no idea what that source is for...

---

### Post by bobpur on 2006-10-11
After a clean install of Ubuntu (and there have been a few) I enable the repositories and follow the directions on the website. Automatix installs with no problems. It's one of the few things I can do well now:)

---

