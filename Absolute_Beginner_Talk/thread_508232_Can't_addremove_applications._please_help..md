---
title: "Can't add/remove applications. please help."
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Jcorns on 2007-07-24
I am an absolute beginner, and when i try to install some applications, i get an error message.

"failed to check for installed and available updates"

I have tried to enter both "sudo apt-get update" and "sudo apt-get install" but neither of them work. 

I've looked around on google, and forums to try and find an answer, but everything has either been way beyond my ubuntu understanding, or has not worked. 


Please somebody help. I couldn't stand to go back to windows!!!

---

### Post by AlexenderReez on 2007-07-24
hm...follow this guide --->

> [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

:)

---

### Post by benx009 on 2007-07-24
> **Jcorns said:**
> I am an absolute beginner, and when i try to install some applications, i get an error message.

"failed to check for installed and available updates"

I have tried to enter both "sudo apt-get update" and "sudo apt-get install" but neither of them work. 

I've looked around on google, and forums to try and find an answer, but everything has either been way beyond my ubuntu understanding, or has not worked. 


Please somebody help. I couldn't stand to go back to windows!!!

are you absolutely sure your internet connection is properly detected and working in ubuntu?

---

### Post by Jcorns on 2007-07-24
I think so, I connect to my own personal network, and I can get onto gaim, and firefox fine.

I'll try the guide. thanks alot.

---

### Post by Jcorns on 2007-07-24
The guide is good, and will lead me to a good kind of last resort type way of doing what I need. But I want the add/remove application to work how it's supposed to, as it can get a lot of things easily. 


Thanks a lot for the advice though. I'll definitely use it. 

With that said....anyone one else got any ideas for me?

---

### Post by Jcorns on 2007-07-24
please help!

---

### Post by mlentink on 2007-07-24
In Appplications>accesories>terminal please type
```
sudo apt-get update
```
Does it complete? If you get an error message, please post it here
then type
```
sudo apt-get upgrade
```
Do you get an error? If so, please post it here.
Aftre which you could do:
```
sudo cat /etc/apt/sources.lst
```
and paste the output here
 Then we can look further into your issue

---

### Post by Jcorns on 2007-07-24
when i use "sudo apt-get update" i get no error message, and it seems to finish that okay.


using "sudo apt-get upgrade" I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  smbclient: Depends: samba-common (= 3.0.24-2ubuntu1) but 3.0.24-2ubuntu1.2 is installed
E: Unmet dependencies. Try using -f.



and when using "sudo cat /etc/apt/sources.lst" I get:

cat: /etc/apt/sources.lst: No such file or directory




Hopefully this means something to you, and is an easy fix. it's pretty much gibberish to me.

---

### Post by irish_flu on 2007-07-24
> **Jcorns said:**
> 
and when using "sudo cat /etc/apt/sources.lst" I get:

cat: /etc/apt/sources.lst: No such file or directory


I think that must have been a typo (it's missing the "i" in list at the end).  The file is sources.list, hence

```
sudo cat /etc/apt/sources.list
```

---

### Post by Darmak on 2007-07-24
I'm having a similar problem, only whenever I try and download updates or use apt-get for anything, it gives me this error message:

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_7.2_all.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
```

Anyone have an idea of what's going on?

---

### Post by Jcorns on 2007-07-24
> **irish_flu said:**
> I think that must have been a typo (it's missing the "i" in list at the end).  The file is sources.list, hence

```
sudo cat /etc/apt/sources.list
```



I got this as a return to that:
> 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

---

### Post by Jcorns on 2007-07-25
can anyone help?

---

### Post by Jcorns on 2007-07-27
anybody....help....please.

---

### Post by ellgor on 2007-07-27
> **Jcorns said:**
> when i use "sudo apt-get update" i get no error message, and it seems to finish that okay.


using "sudo apt-get upgrade" I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  smbclient: Depends: samba-common (= 3.0.24-2ubuntu1) but 3.0.24-2ubuntu1.2 is installed
E: Unmet dependencies. Try using -f.



and when using "sudo cat /etc/apt/sources.lst" I get:

cat: /etc/apt/sources.lst: No such file or directory




Hopefully this means something to you, and is an easy fix. it's pretty much gibberish to me.

Hi,

Had similar problems with a different package but here is my fix:

Set up Synaptic manager and click on mark upgrades and then apply, the usual list of issues relating to whatever package it is your trying to sort is displayed and you click to close that little screen.
If you look at the applications window the offending package should be highlighted in yellow, right click on the package and in the options list that appears check the mark for complete removal, do this for any other offending package and click apply (heart in mouth when I did this as it was the KDE base lib) if all goes well error should be fixed. By any chance do you have Clamav and its family installed, I'm sure I read somewhere about it giving problems, anyway I deleted it at the same time and lo and behold I'm fixed, hope this is of help.

Regards, Ellgor.

---

### Post by Jcorns on 2007-07-28
...I figured it out!!!

Thanks a lot to everyone who cared/helped.


I couldn't have done it with out you all.

ellgor is my savior

---

