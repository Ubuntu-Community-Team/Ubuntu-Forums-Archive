---
title: "local Mirrors"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Nolander on 2007-03-25
Hi all

while browsing i found some thing excelent(for iinet users). it was the iinet ubuntu mirror. there is just one thing.... i dont know wat to do now. 


can any one help me with all the repositorys and scoures.list and stuff cos my clueless

ta,
Nolander.

---

### Post by useResa on 2007-03-25
> **Nolander said:**
> Hi all
while browsing i found some thing excelent(for iinet users). it was the iinet ubuntu mirror. there is just one thing.... i dont know wat to do now. 

can any one help me with all the repositorys and scoures.list and stuff cos my clueless
ta,
Nolander.
Hi Nolander,

Not sure how advanced you are as user, so if I provide too much information: Sorry in advance. Furthermore, based on your user information, I assume you are a **Dapper** user and my answer is based on this.

In order to modify your sources.list, start up a terminal (Applications --> Accessories --> Terminal).
Maybe, just to be sure, you want to make a copy of your current sources.list first.
To do so, type
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```This will create a copy of your current sources.list named sources.list.backup

Now type
```
gksudo gedit /etc/apt/sources.list
```This will open your sources.list in a Text Editor.

Your current sources.list will have various entry lines which (most likely) will contain
> [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)You can replace this (for the most lines AFAIK) with the following
> [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/)So for example, you can change
> dep [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restrictedinto
> dep [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) dapper main restrictedYou can find additional information about this in the Ubuntu Wiki on the [AustralianTeam/LocalAptMirrors]("https://wiki.ubuntu.com/AustralianTeam/LocalAptMirrors") page.

I hope this will help you.

---

### Post by Nolander on 2007-03-26
is this correct:
> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) dapper main restricted universe multiverse
deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) dapper-security main restricted universe multiverse
deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) dapper-backports main restricted universe multiverse

ta,
Nolander.

---

### Post by useResa on 2007-03-26
Seems OK to me. Have you already tried the following command (from terminal) to update your list?
```
sudo apt-get update
```

---

