---
title: "VLC installation problem...conflict"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by ramuntu on 2007-04-12
I am very new in linux. it`s been just 4 days..in these 4 days i learnt lots of things from this forum.. 
for 3 days i have been trying to watch divx,avi,mov video formats on ubuntu6.10. but i couldnot instal required codecs and player..
i realised VLC recognizes most video formats. but i could not install it...
I got the error message when i want to instal VLC player by using `Add/Remove`.

[B][COLOR="Red"]Cannot install 'vlc'

This application conflicts with other installed software. To install 'vlc' the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict.[/COLOR][/B]

[COLOR="Black"]Also i attached the error screen shot. [/COLOR]

i  want to listen also mp3 files.which program shoul i use..most app. in Add/Remove cannot be installed to my `computer type (i386)`. this is what written in the explanation box..
could you please help me.....

---

### Post by taurus on 2007-04-12
Can you post the output of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install vlc
```

---

### Post by ramuntu on 2007-04-12
Actually I had tried these codes before. i found them in the forum.
nontheless i tried again.this is the result..
```
~$ sudo aptitude update
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Get:1 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]           
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                       
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US         
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                        
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                  
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                              
Get:3 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release.gpg [191B]                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                    
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Translation-en_US              
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg                                  
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                  
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
  425 HTTP Error [IP: 91.189.88.31 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
  425 HTTP Error [IP: 91.189.88.31 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
  425 HTTP Error [IP: 91.189.88.31 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
  425 HTTP Error [IP: 91.189.88.31 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
  425 HTTP Error [IP: 91.189.88.31 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
  425 HTTP Error [IP: 91.189.88.31 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
  425 HTTP Error [IP: 91.189.88.31 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
  425 HTTP Error [IP: 91.189.88.31 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
  425 HTTP Error [IP: 91.189.88.31 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release     
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
  425 HTTP Error [IP: 91.189.88.31 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
  425 HTTP Error [IP: 91.189.88.31 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
  425 HTTP Error [IP: 91.189.88.31 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
  425 HTTP Error [IP: 91.189.89.8 80]
Fetched 3B in 35m5s (0B/s)
Reading package lists... Done

```

---

### Post by taurus on 2007-04-12
Did you have synaptic or Add/Remove running while you ran that first command?

Any change you have a proxy on your machine?

---

### Post by Bachstelze on 2007-04-12
Could you please paste your sources.list ? I think we'll find something interesting in there.

---

### Post by ramuntu on 2007-04-12
yes.it was updating..
is that a problem?

---

### Post by ramuntu on 2007-04-12
`Pasting your sources.list`
Sory u know ' am really new. How can i get source list.?

---

### Post by taurus on 2007-04-12
Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by ramuntu on 2007-04-12
**Source List**

```
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://ke.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://ke.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ke.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://ke.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse #Added by software-properties
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://security.ubuntu.com/ubuntu/ edgy-security restricted main universe
deb-src http://security.ubuntu.com/ubuntu/ edgy-security restricted main universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ edgy-updates restricted main universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates restricted main universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main multiverse universe

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt edgy main

deb http://www.getautomatix.com/apt edgy main

deb http://archive.canonical.com/ubuntu edgy-commercial main

deb http://archive.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ edgy universe
#AUTOMATIX REPOS END

```

---

### Post by taurus on 2007-04-12
Shutdown Add/Remove, synaptic, or whatever else you have running right now.  Then, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the # in front of those six lines that have deb in front.

```

deb http://ke.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://ke.archive.ubuntu.com/ubuntu/ edgy universe

deb http://ke.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://ke.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```
Save the changes and run

```
sudo aptitude update
sudo aptitude install vlc
```

---

### Post by Bachstelze on 2007-04-12
That could make things even worse, this sources.lisr was tainted by The-Script-Which-Must-Not-Be-Named, I recommend going back to a clean one ASAP !

---

