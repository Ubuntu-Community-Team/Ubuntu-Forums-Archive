---
title: "Error in Synaptic Manager"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by indie56 on 2006-09-05
Hello
I was adding extra repositories as given in Dapper Guide.
Thereafter in the Synaptic Manager I get the following error-   

E: Malformed line 32 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

How do I overcome this problem
Thanx

---

### Post by monktbd on 2006-09-05
do
> gksudo gedit /etc/apt/sources.list

search for line 32
and paste it here.
or put a # in front to comment it.

---

### Post by indie56 on 2006-09-05
I did that and got- 
(gedit:8790): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Thereafter a window opens -

## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security multiverse universe main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates multiverse universe main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf)
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)

Next step?
Thanx

---

### Post by monktbd on 2006-09-05
put a # in front of the following lines:
(i put them there already)

> **indie56 said:**
> 
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
#deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf)
#deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf)
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)


did you use 
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)
?

if so you missed to add the branches of the repository like main, restricted, free, non-free etc.

these are important as well.

---

### Post by indie56 on 2006-09-05
I did that and the error repeats.
I was trying to install Real player as given in the guide. I added extra repositories as stated and those 5 lines.
I am not aware of line based commands. 
If I insert the Ubuntu CD will it repair itself?
Thanx

---

### Post by monktbd on 2006-09-05
you will need to search which line is line 32 in your sources.list file.

delete that line or comment it with a # in front.
if the error continues delete all the repositories you added to the ubuntu sources.list file.

search these forums here for a proper sources.list file if you cannot resolve the problem.

---

### Post by Jose Catre-Vandis on 2006-09-05
You are repeating this line:
```
deb http://packages.freecontrib.org/ubuntu/plf
```
which is probably creating the error, take onof them out or use a # and retry

---

### Post by indie56 on 2006-09-05
How do I access the source list?

---

### Post by monktbd on 2006-09-05
> **indie56 said:**
> How do I access the source list?

as i wrote above:
> **monktbd said:**
> 
gksudo gedit /etc/apt/sources.list


---

### Post by indie56 on 2006-09-05
I ran the command and got -
 (gedit:17945): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Another window opens -

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
#deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf)
#deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf)
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

When I ran Synaptic I got -
E: Malformed line 22 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
Thanx

---

### Post by monktbd on 2006-09-05
> **indie56 said:**
> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
#deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf)
#deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf)
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)


there are some comments missing.
you can also delete these lines altogether.

please read 
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)
and do some matching of the lines written there and some of the lines in your sources.list.

---

### Post by indie56 on 2006-09-05
Thanx. Synaptic now works.
The problem started when I was trying to install Real Player.
How do I install Real Player?
I have tried various methods listed in these forums. None has worked.

---

### Post by monktbd on 2006-09-05
> **indie56 said:**
> Thanx. Synaptic now works.
The problem started when I was trying to install Real Player.
How do I install Real Player?
I have tried various methods listed in these forums. None has worked.

i am sure installing or trying to install real player didnt mess your sources.list.

i cannot help much with real player since i dont like it at all. 
too much ad infested for me :).

some real codecs are playable with mplayer i think but not all of them. not 100% sure though.

---

