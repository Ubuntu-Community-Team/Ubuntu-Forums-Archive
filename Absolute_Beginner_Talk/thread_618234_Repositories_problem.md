---
title: "Repositories problem"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-11-20
Hi I first of all was prompted to update koffice. Well parts of it but wanted to remove it anyway so I did in synaptic but i am still being prompted to update parts of koffice. Well until now when i went into synaptic and change some things in the repositories and now it seems it locked. When I open synaptic this is what I get:
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

I still don't know how to change the sources.list without help. Sorry I know I have done it a couple of times but I can't remember.

Oh and all i changed in the repositories before I got this error is is the first tab, the last option was filled with a '-' and I deleted that. Well I first ticked it then deleted it. Also in the 'internet updates' tab. I checked 'proposed updates' and then unchecked it. Oops ok and I changed how often you get updates to every two weeks.

Anyone got an idea how I stuffed up?

---

### Post by PmDematagoda on 2007-11-20
Post your sources.list file using:-

```
cat /etc/apt/sources.list
```

---

### Post by rapattack1 on 2007-11-20
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted 

## Major bug fix updates produced after the final release of the 
## distribution. 
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe' 
## repository. 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## universe WILL NOT receive any review or updates from the Ubuntu security 
## team. 
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe 

## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe 


## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.) 
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) edgy free non-free 
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu 
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main 

## Listen 
# deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen

I also just opened the sources.list.orig and it is different.

---

### Post by rapattack1 on 2007-12-09
Is there no one that can help? I opened my laptop again and the problem is still there. It seems I can't get on the net either with it. I don't know why. I open firefox and it looks like it is going to connect but does not.:confused:

---

### Post by taurus on 2007-12-09
There is something wrong with the second line of your /etc/apt/sources.list.d/edgy-universe.list, NOT /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list.d/edgy-universe.list
```

---

### Post by rapattack1 on 2007-12-09
Oh ok. I don't know which is which but here is what I got when I did that command you posted-

# automatically added by gnome-app-install on 2007-11-05 22:13:48.995327 
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security 
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates universe

---

### Post by taurus on 2007-12-09
> **rapattack1 said:**
> Oh ok. I don't know which is which but here is what I got when I did that command you posted-

# automatically added by gnome-app-install on 2007-11-05 22:13:48.995327 
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security 
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates universe

You need to put a # in front of the second line to comment it out.

```

# automatically added by gnome-app-install on 2007-11-05 22:13:48.995327
**[COLOR="Blue"]#[/COLOR]**deb http://au.archive.ubuntu.com/ubuntu/ edgy
deb http://security.ubuntu.com/ubuntu edgy-security
deb http://au.archive.ubuntu.com/ubuntu/ edgy-updates universe

```

---

### Post by rapattack1 on 2007-12-09
Thanks that did it I am back on the net but I can't get any updates. Here is what I get when I do apt-get update:
carolyn@carolyn-laptop:~$ apt-get update
E: Malformed line 3 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
carolyn@carolyn-laptop:~$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
carolyn@carolyn-laptop:~$

---

### Post by taurus on 2007-12-09
First, you need to run those commands as root so you need to put a sudo in from of them.

```
**sudo** apt-get update
**sudo** apt-get upgrade
```
However, before you run those two commands, you need to edit /etc/apt/sources.list.d/edgy-universe.list 

```
gksudo gedit /etc/apt/sources.list.d/edgy-universe.list
```
and place a # in front of all the lines in there to comment them all out.  Save it and then run the two commands from above.

---

### Post by rapattack1 on 2007-12-09
oops but I am still getting the same thing

carolyn@carolyn-laptop:~$ sudo apt-get update
E: Malformed line 3 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
carolyn@carolyn-laptop:~$ sudo bash
root@carolyn-laptop:~# apt-get update
E: Malformed line 3 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)

OOops again....i didn't read the whole post. Now I can update and upgrade. Thanks so much!

---

### Post by taurus on 2007-12-09
Okay, I am going to repeat this one more time because apparently, you didn't even bother to read my previous message completely.  

You need to edit /etc/apt/sources.list.d/edgy-universe.list 

```
gksudo gedit /etc/apt/sources.list.d/edgy-universe.list
```
and place a # in front of all the lines in there to comment them all out.  Save it and then run those two commands again.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by PmDematagoda on 2007-12-09
taurus, just a question, couldn't the problem be solved simply by removing the file in question?

---

### Post by rapattack1 on 2007-12-09
Hi tauras sorry I did the command earlier and edited my post but apparently not quick enough. Thanks again all is well and working now!!!

OK so I have a lot more to learn so I will try and get to understanding what that file means as I am just not understanding all aspects of the repositories yet! I get what it isabout but there are too many bits and pieces that I don't get.
Thanks rap attack

---

