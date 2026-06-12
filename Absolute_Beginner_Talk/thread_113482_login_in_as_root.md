---
title: "login in as root"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by mwanafunzi on 2006-01-06
hi guys, I have a small problem. I have been trying to install ndiswrapper so that I am able to use my minitar wireless card (as this is the only way I can access the net with kubuntu). I have downloaded ndiswrapper and i have the widnows driver .inf file. The problem I am having is that I am not able to get into my root account. I have tried using the su command, sudo command and I have even tried login on as root. Any suggestions (hopefully other than reinstalling kubuntu)? I am pretty sure that I am typing in the right password. 
I had another question. Would i need to install gcc as well so as to compile ndiswrapper?

---

### Post by bluefrog on 2006-01-06
ndiswrapper on the cd. no need to compile.

on normal install sudo is used.

james

---

### Post by byen on 2006-01-06
yes as bluefrog mentioned here you do not have to login as a sudo user. all you have to do is enter "sudo" before the command. for example. To install a program. you would go:
sudo apt-get install <packagename>

Also you do not have to install the ndiswrapper.. it comes in the Ubuntu install cd. And just to make this easy here is a link you might be interested in:
[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)
hope that helps.goodluck

---

### Post by mwanafunzi on 2006-01-07
thanks for you help. I managed to install ndiswrapper. I did this through package manager (adept). I spent a couple of hours after that trying to configure my card. I think i made a mistake somewhere. I will follow the instructions to the link. Hopefully this time I will get it right. Curiously, is apt-get used for any sort of install i.e. I thought apt-get was only used if you were installing of the net. ?

again thanks for the help. I have to say I really likke the ubuntu community.

---

### Post by Mustard on 2006-01-07
The dpkg command is used for installing .deb packages locally.  Apt-get downloads from whatever sources you have listed in your /etc/apt/source.list, which as a general rule are online repositories.  It does have your install CD listed in there too however (or normally does when you first install), so it would install from CD as well, assuming the package you were after exists on the CD.

---

