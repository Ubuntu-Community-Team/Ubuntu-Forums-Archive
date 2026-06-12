---
title: "Emesene wont install .... help ?"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by moehabibi on 2008-04-17
hii 
i download emesene 1.0 from the site 

i went to ubuntu and downloaded a file name 

emesene_1.0-dist-1_all.deb 

but when i press it .. the packager installer gives me an error in the packager Installer 


__________________________________________________________________
Package: emesene

status : " [COLOR="Red"]Error: Dependency is not satisfiable : python - central[/COLOR]

Description | Detials | Included files 


BLA BLA 
________________________________________________________________________

im not sure waht to do .. i tried downloading a source file and was searchign around on how to install from source
 
 but to tel lyou the truth .. all those script commands and shyt really got me confusing ...

can someone please tell me what to do to fix this error 

or if give me a detialed guide on how to install it threw the terminall 

please be REALLY detialed .. ... cuz a simple instruction like " put the emence fold in apt " can mess me up cuz when i try to drag it into that folder it gives me an error saying i cant do that ... 

thanks ALOT guys ..

---

### Post by forestpixie on 2008-04-17
Open a terminal and paste this in 

```
sudo apt-get install emesene
```

enter password when prompted

---

### Post by moehabibi on 2008-04-17
moe@Moe-Desktop:~$ sudo apt-get install emesene
[sudo] password for moe:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package emesene
moe@Moe-Desktop:~$ 

dats what i get .... 

couldnt find package .. 

where do i put the package ? and HOW ?

---

### Post by forestpixie on 2008-04-17
Have you set up software sources yet? Open in System > Admin. Tick all boxes except sources and cd-rom, go to 3rd party tab and tick partner box - close and reload and try command again.

If you have got software sources set up - paste this command in to terminal, enter and paste whole ouptput here please.

```
cat /etc/apt/sources.list
```

---

### Post by moehabibi on 2008-04-17
moe@Moe-Desktop:~$ sudo apt-get install emesence
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package emesence
moe@Moe-Desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


______________________________________________________________

as you can see i tried puttting the sudo apt-get insta...... command agian .. 
it didnt workk ... 

i pasted the outcome of the other command .. i have no idea waht it is ... 

but you said you wannted to see it .. soo there it is ... 

soo what do i do next :S ?

---

### Post by forestpixie on 2008-04-17
You've got a typo - paste the first command I gave you into terminal and try again.

Should be fine after that - can you mark thread solved assuming it is :)

---

### Post by moehabibi on 2008-04-17
moe@Moe-Desktop:~$ sudo apt-get install emesene
[sudo] password for moe:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package emesene
moe@Moe-Desktop:~$ 


okayy there ... typoo is fixedd ... 
but problem isnt :(

---

### Post by forestpixie on 2008-04-18
Ok - very tired last night. The repo version is in hardy not in gutsy so that won't work for you as it is - you say you downloaded the source, once that is unpacked go to the directory in a terminal and do 

```
./emesene
```
and it will run. It is always worth looking in the extracted package for readme's or doc's.

You can set a launcher for it - right click desktop, add launcher, put a name in the box and then browse to the emesene file in the extracted directory.

---

### Post by Mazza558 on 2008-04-18
It's easier than that! 

> sudo apt-get install python-central

then open the emesene package again.

---

### Post by i-Buntu-dk on 2008-06-13
I have tried both Pidgin and Emesene for IM to acces my MSN Messenger account. It works, but there is a lot of the functinality from Messenger there sadly is lost.
Do anyone know if webcam chat is posible from Emesene/Pidgin to MSN Messenger/Live messenger?
I use MSN Messenger webcam regularly to talk to both my sister and parents, and I really hate to have to boot in win XP just to talk to them and then booting back into Ubuntu..
btw...this thing rocks...

---

