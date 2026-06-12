---
title: "Once again a noob in shores of trouble"
date: 2005-05-30
forum: Absolute Beginner Talk
---

### Post by Latz on 2005-05-30
Ok, yesterday I readed the manual of 'greedyturtle' and learned a bit of using command promt and so on, but I have alot (atleast I think so) to do before I could use my computer well. 

So here is my 'list to do':
[list=1]
[*]Mount my hard disks.
[*]Learn how to install items into ubuntu.
[*]Learn how to make this old computer a server.
[*]And at last, I want to know how to install and play my fav game, Warcraft III + TFT. Over Battle.net.
[/list] 

I could have tried installing Irssi and other programs on my computer, but first I want to mount the disks. And do I have to install all the programs into the hard disk where ubuntu is installed into? Aaaand, nothing for now. You dont have to tell everything at once, you can just start by telling how to mount hd's.  :razz:

---

### Post by stepper on 2005-05-30
[http://www.ubuntuguide.org](http://www.ubuntuguide.org) can answer allmost all of your questions.

---

### Post by Latz on 2005-05-30
Okay, I just mounted my harddisks succesfully.  \\:D/ 
But how should I install programs like amaroK and irssi? Where to extract the files and how to install, atleast the install file that 'should' help didn't help at all. Just would you tell a 'logical' way how to do installs, and how do you know that what package you have to download through command promt and what it is called?

---

### Post by kvidell on 2005-05-30
[QUOTE=Latz]Okay, I just mounted my harddisks succesfully.  \\:D/ 
But how should I install programs like amaroK and irssi? Where to extract the files and how to install, atleast the install file that 'should' help didn't help at all. Just would you tell a 'logical' way how to do installs, and how do you know that what package you have to download through command promt and what it is called?[/QUOTE]
 Refer again to that guide for installation help :)
But for a pointer:```
man apt-get
```Type that in to a terminal and start reading.
Useful info is abundant there.

---

### Post by Latz on 2005-05-30
Ok.. I try to install nano, but here comes the error! "There is no such a file or directory." In translated from my native language. So could you tell me good, and working sources for my sources.list?

---

### Post by kvidell on 2005-05-30
[QUOTE=Latz]Ok.. I try to install nano, but here comes the error! "There is no such a file or directory." In translated from my native language. So could you tell me good, and working sources for my sources.list?[/QUOTE]
 How did you try to install it?```
portakel:/etc/apt# apt-get install nano
Reading package lists... Done
Building dependency tree... Done
nano is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```Worked fine for me. (Granted it was already installed)

And just for kicks, this is my sources list:```
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main
#deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
#deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

#backup Mirror - FAST
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
```Hope that helps some,
- Kev

---

### Post by Latz on 2005-05-30
My filelists were just down or something. I have the newest version too, but I just wanted to try installing nano.

---

### Post by Latz on 2005-05-30
Aaargh!
This playing as root is making me crazy! Everyone says, that you can press a button with right click and then there is something like "open as root" or something, but I dont find a **** about that command. And if I try to install something it just gives me 10 errors, ERROR ERROR PUERTO RICO ALL WRONG! and it starts to cry that I am not the root, and it never asks the password of root or something!

---

### Post by Latz on 2005-05-30
Ok, I worked that out, but now I can do absolutely nothing without your help. When I start computer it says:

Koneen  Internet-osoite ei selvinnyt,
mikä estää Gnomea toimimasta kunnolla.
Ongelman korjaaminen saattaa olla mahdollista lisäämällä
tiedostoon /etc/hosts.

In English it would be something like this:

Internet-address of your computer did not clear up,
and it denies Gnome to work well.
Correcting the problem might be possible by adding to file /etc/hosts.

It just says that it might clear up by adding (WHAT?) something into /etc/hosts. First bad thing is, that I cant log in as root and therefore, I cannot edit the file.

The file is like this:

127.0.0.1 localhost.localdomain localhost kissanhiekkalaatikko 

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
195.74.0.47 kanetti3577

So the name of the computer is kissanhiekkalaatikko, and if I go into command promt, it's just 'ville@(absolutely nothing)'

Would you help me fastly, thanks already to those who will help.

---

