---
title: "need some help with: sudo apt-get install sun-j2re1.5"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by cyrix on 2005-08-21
sudo apt-get install sun-j2re1.5
is this the correct syntax to get java to download and install? Every time I do this it comes back with the following: 

john@ubuntujohnboy:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5
john@ubuntujohnboy:~$


I already added the other repositories as suggested and already did: sudo apt-get update

sudo apt-get install sun-j2re1.5  <<< should there be something else here? 


I am not sure what else to do at the moment. 

thanks in advance for your help...

---Cyrix

---

### Post by jasmuz on 2005-08-21
Verify that in your sources list these repositories are added:

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

then type sudo apt-get update

then sudo apt-get install sun-j2re1.5

---

### Post by cyrix on 2005-08-21
I got it working, thank you!

---

### Post by vassalle on 2005-08-23
hi, ive added the caliu repo in but i still cant install the file.. ive tried mirrormax, ubuntu official backport and caliu.. all of them dont have this file.. any ideas ?

vassalle@vassalle:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5

---

### Post by tenn on 2005-08-23
I have done what is above as well, and I still cant get this bloody java going it the same with every version of linux I try its driving me nuts it the only problem I run into that I cant seem to work out, I have followed the instructions at java site word for word with jre-1_5_0_04-linux-i586.bin and than I have tried what firefox said about putting links in the plugin folder  ](*,)   :???:

---

### Post by evansa4 on 2005-08-23
have you edited your updates thing

---

### Post by chi on 2005-08-23
im having the exact same problem as vassalle and tenn and cyrix.  i have installed every repository i could get my hands on   ](*,) 

root@infected:/home/chi # apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5

EDIT:
could it have something to do with the kernel headers?
im wondering this because thats the only diffrence between two computers here..

---

### Post by Kapre on 2005-08-23
[QUOTE=chi]im having the exact same problem as vassalle and tenn and cyrix.  i have installed every repository i could get my hands on   ](*,) 

root@infected:/home/chi # apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5

EDIT:
could it have something to do with the kernel headers?
im wondering this because thats the only diffrence between two computers here..[/QUOTE]

Chi - are doing this in "sudo" mode? I didn't have problems installing it. Maybe your repo list is not updated? Just wonderin.

K

---

### Post by ajiva on 2005-08-24
[QUOTE=Kapre]Chi - are doing this in "sudo" mode? I didn't have problems installing it. Maybe your repo list is not updated? Just wonderin.

K[/QUOTE]

I think the Java packages have been removed.  Because I saw it a few days ago, but because of the size didn't download it.  Now its gone...

---

### Post by tenn on 2005-08-24
I finaly got it going after following the java install instructions for the jre-1_5_0_04-linux-i586.bin file and than I did this, 

fakeroot make-jpkg --full-name "<Your name>" --email "<Your email>" jre-1_5_0_04-linux-i586.bin

and than run the deb file its working now.

---

