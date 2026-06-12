---
title: "need help installing java runtime environment for runescape"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by i am the nob on 2006-12-14
hi i just got ubuntu and i really need help downloading the plugin for runescapei think its java runeime envirment ive tryed using a different browser ive tryed clearing my chatch ive tryed auto matix ive tryed synaptic package manenger ive added all the extra respetories,when ever i get close to a prosess of downloading java it says dpkg was interrupted, you must manually run 'dpkg --configure -a and sun-java5-jre:
 Depends: sun-java5-bin (=1.5.0-06-1) but it is not installable or
 	ia32-sun-java5-bin (=1.5.0-06-1) but it is not installable 

pleese help im running out of options thanks](*,)

---

### Post by taurus on 2006-12-14
Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
```
Then install automatix2 and use it to install java and other goodies on your machine then!

[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29)

p.s.  Make sure you have enable both universe & multiverse in your /etc/apt/sources.list first...

---

### Post by scrooge_74 on 2006-12-14
> **i am the nob said:**
> hi i just got ubuntu and i really need help downloading the plugin for runescapei think its java runeime envirment ive tryed using a different browser ive tryed clearing my chatch ive tryed auto matix ive tryed synaptic package manenger ive added all the extra respetories,when ever i get close to a prosess of downloading java it says dpkg was interrupted, you must manually run 'dpkg --configure -a and sun-java5-jre:
 Depends: sun-java5-bin (=1.5.0-06-1) but it is not installable or
 	ia32-sun-java5-bin (=1.5.0-06-1) but it is not installable 

pleese help im running out of options thanks](*,)

You can also go to [http://www.java.com](http://www.java.com) and follow the instructions for a manual install is not too difficult and in the long run will help you have a better understanding of how you do things  in Linux in general

---

### Post by pesach on 2007-01-23
My problem is very similiar.  I try to run runescape but it always tells me I have missing plugins. I click install missing plugins and it brings up "java runtime enviroment".  When I hit install, it tells me that it isnt avaiable and I should manually install it. It gave me four options of installing.  I tried installing each one and the file came up on my desktop I clicked on it and this came up:
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.
 I tried all the character codings and nothing worked
The I tryied using Synaptic package manager.  I searches java runtime enviroment and installed the package that came up.  This did nothing.
  I installed automatix2 and installed all the java applications they have available. Still nothing.  It seems to me that I have tried absolutely everything.
Im not sure if this is imporant but I am using a 64-bit processor
Help would be greatly appreciated

---

### Post by minisori on 2007-01-24
If i dont remember bad, after install jre from synaptic, you need to install also the mozilla plugin. Not sure since i can not check it right now.

---

### Post by kerry_s on 2007-01-24
You just need to enable all the repos then->
sudo apt-get update
sudo apt-get install sun-java5-plugin

and it will pull in everything else. My sons so addicted to that game.

---

### Post by pesach on 2007-01-24
> **kerry_s said:**
> You just need to enable all the repos then->
sudo apt-get-update
sudo apt-get install sun-java5-plugin

and it will pull in everything else. My sons so addicted to that game.
this is what I got...
pesach@LinuxRules:~$ sudo apt-get-update
sudo: apt-get-update: command not found
pesach@LinuxRules:~$ sudo apt-get install sun-java5-plugin
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

not sure what that means

---

### Post by kerry_s on 2007-01-24
My bag, it's> sudo apt-get update < no dash in front of update
make sure you don't have synaptic or add/remove open, only 1 install program at a time.

---

### Post by pesach on 2007-01-24
hmmm. now what I got is:
pesach@LinuxRules:~$ sudo apt-get install sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
Package sun-java5-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java5-plugin has no installation candidate

---

### Post by pesach on 2007-01-24
> **pesach said:**
> hmmm. now what I got is:
pesach@LinuxRules:~$ sudo apt-get install sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
Package sun-java5-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java5-plugin has no installation candidate

by the way i got this even b4 i got rid of that dash.  the first terminal quote only happened once I think, the when I tried it again above is what happened

---

### Post by kerry_s on 2007-01-24
Lets see your /etc/apt/sources.list cause it's looking like you don't have all the repos on. Here's what i use->

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe

---

### Post by pesach on 2007-01-24
> **kerry_s said:**
> Lets see your /etc/apt/sources.list cause it's looking like you don't have all the repos on. Here's what i use->

Im kinda new to the whole ubuntu thing so im not really sure what that means.

> **kerry_s said:**
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
I click on the link... and then what?
*sorry for being such a newbie here*:redface:

---

### Post by pesach on 2007-01-24
> **kerry_s said:**
> Lets see your /etc/apt/sources.list cause it's looking like you don't have all the repos on. Here's what i use->
oh is that for terminal? this is what I got when I entered that in terminal
bash: /etc/apt/sources.list: Permission denied

---

### Post by kerry_s on 2007-01-24
Sorry, press alt + F2 and type> gedit /etc/apt/sources.list  <then copy and paste that here so we can see what repos your using to get applications.

---

### Post by pesach on 2007-01-24
Its kind of long, but here goes:
```
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release amd64 (20060531)]/ dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://www.getautomatix.com/apt dapper main

#AUTOMATIX REPOS START

deb http://ubuntu.moshen.de dapper misc

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
#AUTOMATIX REPOS END
```

---

### Post by lingnoi on 2007-01-25
Sorry to kind of take this post into a different direction.

I was just reading and I thought the JRE was GPLed now so should there not be some kind of deb package to make installing java easier?

---

### Post by kerry_s on 2007-01-25
> **pesach said:**
> Its kind of long, but here goes:
```
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release amd64 (20060531)]/ dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted



# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://www.getautomatix.com/apt dapper main

#AUTOMATIX REPOS START

deb http://ubuntu.moshen.de dapper misc

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
#AUTOMATIX REPOS END
```

Okay not all your repos are on, you want to turn these 3 on. Change these 3 lines->

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

to

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


To do this press the alt + F2 and type> sudo gedit /etc/apt/sources.list <this will give you root privileges to edit it, then just uncomment those 3 lines. exit and save

now in terminal run->
sudo apt-get update
sudo apt-get install sun-java5-plugin

That's it your done, enjoy  your runescape.

---

### Post by kerry_s on 2007-01-25
> **lingnoi said:**
> Sorry to kind of take this post into a different direction.

I was just reading and I thought the JRE was GPLed now so should there not be some kind of deb package to make installing java easier?

It is easy to install as long as all your repos are on, it's just a apt-get or synaptic away. synaptic you just click mark for installation and apply, how hard is that. On the command line it's "sudo apt-get install sun-java5-plugin" bam done. There's nothing to it.

---

### Post by pesach on 2007-01-25
> **kerry_s said:**
> Okay not all your repos are on, you want to turn these 3 on. Change these 3 lines->

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

to

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


To do this press the alt + F2 and type> sudo gedit /etc/apt/sources.list <this will give you root privileges to edit it, then just uncomment those 3 lines. exit and save

I did all this and
> **kerry_s said:**
> now in terminal run->
sudo apt-get update
But when I put this in
> **kerry_s said:**
> sudo apt-get install sun-java5-plugin
I got :
```
Reading package lists... Done
Building dependency tree... Done
Package sun-java5-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java5-plugin has no installation candidate
```

Still not working

---

### Post by pesach on 2007-01-25
would maybe installing swiftfox work?

---

### Post by pesach on 2007-01-25
Well I guess I really did not solve the problem; i kinda avoided it.  I just installed swiftfox along with all of its plug-ins from automatix. Anyway, thanx for all the help guys!!):P

---

