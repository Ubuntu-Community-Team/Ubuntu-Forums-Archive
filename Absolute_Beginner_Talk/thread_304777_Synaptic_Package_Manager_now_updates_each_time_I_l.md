---
title: "Synaptic Package Manager now updates each time I load it for no reason"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by randytuggle on 2006-11-22
I must have done something wrong...I use Synaptic Package Manager a few times a day (I'm a noob, shoot me). Each time I open it, it wants to add about 57 updates that have already been updated time and time before. Is there a fix to this? It's just updating the same stuff over and over...

---

### Post by Bachstelze on 2006-11-22
Hmm, please paste the output of

```
sudo apt-get upgrade
```

---

### Post by randytuggle on 2006-11-22
The computer doing this is at my house. I'm not there right now. I will paste the code from apt-get when I get home this evening. Thanks for the interest in helping me out!

---

### Post by randytuggle on 2006-11-22
> **HymnToLife said:**
> Hmm, please paste the output of

```
sudo apt-get upgrade
```

Here's some interesting pasted terminal stuff. apt-get upgrade offered nothing new - but apt-get update did. I did this twice and got the same results.

randytuggle@randy-ubuntu:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
randytuggle@randy-ubuntu:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources
Fetched 4B in 1s (3B/s)  
Reading package lists... Done

---

### Post by kerry_s on 2006-11-22
It's normal, you just got to read up on apt-get->

sudo apt-get update  <grab a list available packckages, it does not install nothing.

From your output there's nothing to upgrade so you get->
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

"sudo apt-get update" is always done first so you can get the list of packages, so it would be like this->

sudo apt-get update
sudo apt-get upgrade

and if there's anything new it would upgrade.

---

### Post by randytuggle on 2006-11-22
ok, thanks for the help. I appreciate the info.

---

