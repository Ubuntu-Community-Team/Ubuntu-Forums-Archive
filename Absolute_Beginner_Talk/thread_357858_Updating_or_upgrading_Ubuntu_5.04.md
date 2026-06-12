---
title: "Updating or upgrading Ubuntu 5.04"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-02-10
Hi I am concerned that while surfing the net etc that the firewall would be out of date. I have only had Ubuntu on this machine a few weeks and haven't updated anything for two weeks I guess because the respositories is wrong. My friend that installed Ubuntu is very busy so hasn't been over to correct the problem. This is the error when I enter Synaptic:
E:Type 'http://mirror.optusnet.net/ubuntu' is not known on line 29 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by bapoumba on 2007-02-10
Open a terminal (> Accessories > Terminal) and run:
```
cat /etc/apt/sources.list
```
Paste the complete output in here.
Your sources.list has an incorrect line.
[https://help.ubuntu.com/community/Repositories/Ubuntu/Breezy]("https://help.ubuntu.com/community/Repositories/Ubuntu/Breezy")

---

### Post by rapattack1 on 2007-02-10
$ cat /etc/apt/sources.list


## Uncomment the following two lines to fetch updated software from the network
# deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb [ftp://ftp.debian.org/debian/](ftp://ftp.debian.org/debian/) stable main


[http://mirror.optusnet.net/ubuntu](http://mirror.optusnet.net/ubuntu) main universe multiverse

---

### Post by bapoumba on 2007-02-10
Okay,
last line in your sources.list is indeed incorrect. I gave you a link for breezy, as your title stated you were using it. From your sources.list, the only repository you are using is an edgy cd-rom. Before anything, you need to check which version of ubuntu you are actually using.
Please post the output to :
```
uname -a
lsb_release -cd
```

---

### Post by rapattack1 on 2007-02-11
It is definately 5.04. My friend used a 6.10 cd to update or something that is why that is mentioned. He put that line in the repository. He also told me to put the other things that are not working. He hasn't had time to come over to my place and correct this.
uname -a
Linux Carla 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux
carla@Carla:~$ lsb_release -cd
Description:    Ubuntu (The Hoary Hedgehog Release)
Codename:       hoary

---

### Post by bapoumba on 2007-02-11
Okay, you're on Hoary. Couple of questions:
1- do you know if you have a separate /home partition ?
```
cat /etc/fstab
```
2- why did (you or your friend) install Hoary ? This release is not supported anymore
3- do you think you are able to manage a reinstall with a newer release ? If not, we'll fix your sources.list and get you running with Hoary untill your friend is available
4- you should not worry about security. Even out of date, Hoary was a great release (personnal opinion)
5- installing stuff from Edgy (current stable release) on Hoary was not a good idea

---

### Post by rapattack1 on 2007-02-12
Well good news my friend made it over today and he changed the repository through the terminal I guess. I am not familiar with how it all works yet but we got the system updated and now upgrading. Will take a long time as I am on dialup.
He put Hoary on this machine originally because that is the version that was the latest when he went overseas over a year ago. We tried to install it on another machine way back then but anyway it is a bit of a long story. It was a test like thing and eventually I will be using another machine to get on the net that has more ram. This machine doesn't have much ram(128mb). I tried to install Edgy on 2 other machines that had this amount of ram and it was impossible. Then I tried Hoary and it installed. When the right(256 and up) amount of ram was on another 2 machine the installation went fine for Edgy.
So anyway all is well as I am getting what I need now! Thanks as it is always good to learn as I don't know how long I will have access to this friend in person. I need to learn by myself!

Oh I am not sure what a separate home partition is but I won't try to access the terminal right now as I am getting the upgrade thing right now.

---

### Post by bapoumba on 2007-02-12
Okay, feel free to ask any question you have in here too ;)

---

### Post by rapattack1 on 2007-02-12
Thanks will do:)

---

