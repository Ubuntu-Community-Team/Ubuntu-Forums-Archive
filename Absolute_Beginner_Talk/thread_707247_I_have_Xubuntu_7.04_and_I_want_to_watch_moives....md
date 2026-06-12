---
title: "I have Xubuntu 7.04 and I want to watch moives..."
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by zazen666 on 2008-02-25
Can seem to find a clear answer on the forums.
when trying to watch a dvd, I get error message that I need libdvd css?
What is fastest way to install?

---

### Post by LeAstrale on 2008-02-25
hi

this site should do the explaining to you: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

/Astral-1

---

### Post by sayakb on 2008-02-25
@OP

Install VLC player

```
sudo apt-get install vlc
```

---

### Post by zazen666 on 2008-02-25
Hmm......

VLC wont play the movie

and 

and after installing medibuntu and trying to install libdvdcss I get this error

nstall libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libdvdcss2: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by sayakb on 2008-02-25
> **zazen666 said:**
> Hmm......

VLC wont play the movie

and 

and after installing medibuntu and trying to install libdvdcss I get this error

nstall libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libdvdcss2: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Well, do you have Totem Movie Player? If not, install it , plus all the proprietary gstreamer plugins belonging to the good, bad and ugly sets. Btw, DVD files are usually VOB files. VLC plays those files really well. Which media format do you have in your case?

---

### Post by NightwishFan on 2008-02-25
That is odd. Vlc plays any DVD I put in it. My Ubuntu install is clean, codec wise.

---

### Post by LowSky on 2008-02-25
did you run this like it said?

```
apt-get -f install
```

did you install the correct medibuntu repos?

copy and paste all these commands


first
```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

```
then

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

then 

```
sudo apt-get install libdvdcss2

```

then
```
sudo apt-get install w32codecs

```

now it should all work then

---

