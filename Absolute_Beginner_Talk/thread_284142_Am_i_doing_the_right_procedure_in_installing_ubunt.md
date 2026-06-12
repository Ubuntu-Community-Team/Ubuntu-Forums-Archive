---
title: "Am i doing the right procedure in installing ubuntu 6.06"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by rowster27 on 2006-10-25
after doing a fresh install... (whats what..)


A. update synaptic?

B. (use)
   sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
   gksudo gedit /etc/apt/sources.list

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free 


OR
C. install Automatix2

---

### Post by Bachstelze on 2006-10-25
Why not just download the Dapper CD and install from it instead of doing a fresh Breezy install and upgrade - not to mention upgrading to Etch soon.

---

### Post by rowster27 on 2006-10-25
> **HymnToLife said:**
> Why not just download the Dapper CD and install from it instead of doing a fresh Breezy install and upgrade - not to mention upgrading to Etch soon.

i already have a dapper cd. i just wanted to know if im doing the proper way and learn from it. (i want to use dapper for the mean time.)

if edgy eft is release ill order fresh cd's from ubuntu..:)

thank you for the advice HymnToLife.:)

---

### Post by Bachstelze on 2006-10-25
If you want to upgrade : two steps

1) Open your sources.list and replace all occurences of the release name to the next one (e.g. breezy to dapper, dapper to edgy...)
2) sudo apt-get dist-upgrade

voilà :)

Oh btw, sorry to disappoint you but Canonical will not ship free CDs of Edgy ;)

---

### Post by rowster27 on 2006-10-25
> **HymnToLife said:**
> If you want to upgrade : two steps

1) Open your sources.list and replace all occurences of the release name to the next one (e.g. breezy to dapper, dapper to edgy...)
2) sudo apt-get dist-upgrade

voilà :)

Oh btw, sorry to disappoint you but Canonical will not ship free CDs of Edgy ;)

ohh i see sounds reasonable for the LTS. thanks for the info.

(regading to my question what am i going to use step A, B or C?)

thanks again HymnToLife :)

---

### Post by Bachstelze on 2006-10-25
All of them will work I think - don't know Automatix but if they say it works, I guess it does work :p Which one you use is a matter of personal preference. Personnaly, I'd go with B.

---

### Post by rowster27 on 2006-10-25
> **HymnToLife said:**
> All of them will work I think - don't know Automatix but if they say it works, I guess it does work :p Which one you use is a matter of personal preference. Personnaly, I'd go with B.



(after a fresh install an update icon will pop-up stating there are 187 updates available)

should i "update" it first then continue with step B?

OR skip the "update" and continue with step B

(step B sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup &
 gksudo gedit /etc/apt/sources.list)

---

### Post by Bachstelze on 2006-10-25
doing the Breezy updates would be a waste of time since they will be replaced by Dapper's when you upgrade anyway. Don't bother with them and go on editing your sources.list.

---

### Post by rowster27 on 2006-10-25
> **HymnToLife said:**
> doing the Breezy updates would be a waste of time since they will be replaced by Dapper's when you upgrade anyway. Don't bother with them and go on editing your sources.list.

sorry i didnt mention that im using ubuntu 6.06 right now. i was just wondering if it is an essential to update first then edit the source.list..

---

### Post by Bachstelze on 2006-10-25
If you want to upgrade to Edgy, no need to do the Dapper updates first.

---

### Post by rowster27 on 2006-10-25
> **HymnToLife said:**
> If you want to upgrade to Edgy, no need to do the Dapper updates first.


are you using edgy right now? how's it going? would you kindly post your source.list.

---

### Post by Bachstelze on 2006-10-25
No I'm not ;) But I guess just replacing all the occurences of the word 'dapper' to 'edgy' will do the trick, has always worked for me since Hoary.

---

### Post by rowster27 on 2006-10-25
> **HymnToLife said:**
> No I'm not ;) But I guess just replacing all the occurences of the word 'dapper' to 'edgy' will do the trick, has always worked for me since Hoary.

ok thank you. ;)

---

