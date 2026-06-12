---
title: "synaptic and add/remove not launching"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-10-02
so I have been getting rather strange msg when trying to intall from the command line....

i tried to open add/remove to use it... no luck

tried opening synaptic, no luck

both worked yesterday.

tried this in terminal and got the same nasty error I get when trying to install from terminal!
HELP!!!



```
rob@rob-desktop:~$ synaptic
Segmentation fault (core dumped)

```

---

### Post by philinux on 2007-10-02
use this in the terminal

sudo aptitude update

---

### Post by beanco on 2007-10-02
done, still not working though!


robi

---

### Post by aktiwers on 2007-10-02
what about:
```
sudo apt-get -f install
```
and
```
sudo apt-get autoremove
```

---

### Post by beanco on 2007-10-02
so would both of those be removing things?

great to be able to remove from teh command line but I was wondering why neither prgm is launching....

i cannot install anything from the command line at the moment, as my other thread says... i get 

segmentation fault (core dumped)

when I try to install anything.... that is why i wanted to use synaptic.

robi

---

### Post by aktiwers on 2007-10-02
It would only remove packages you dont use anymore. libs and stuff. try them and tell if they worked. Else there are other things to try afterwords.

---

### Post by beanco on 2007-10-02
sorry about being a n00b but are you suggesting i run command number one.

then run command number two and report back here?

just want to be clear

thanks BTW

robi

---

### Post by beanco on 2007-10-02
thoguth I would gvie ti a whilr

go tthis

```
rob@rob-desktop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Segmentation fault (core dumped)

```

after digging  a bit I found a thread that suggested this

> rob@rob-desktop:~$ cat /etc/apt/sources.list

and this is what I got

> 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse


---

### Post by dca on 2007-10-02
That error usually appears if the application you're using has a bug...  Read through this and see if what they refernce helps any...
 
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/72475](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/72475)
 
 
or type this into google search bar:
 
segmentation fault core dump synaptic

---

### Post by philinux on 2007-10-02
What was the last program you installed?

---

### Post by beanco on 2007-10-02
dca,,, i will get to that... thanks


philinux.... Opera was the last... successful installation yesterday... today I tried to install macromedia flash for opera and 3 video editing prgms, none of hwich were a success...

robi

---

### Post by beanco on 2007-10-02
> **dca said:**
> That error usually appears if the application you're using has a bug...  Read through this and see if what they refernce helps any...
 
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/72475](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/72475)
 
 
or type this into google search bar:
 
segmentation fault core dump synaptic


found some work rounds there that seemed to have worked. i have the two prgms installed that I was originally looking for and synaptic opened... still do not know how to use it, but it is open...


this was what did it for me


> sudo rm /var/cache/apt/*.bin

again, thanks

robi

---

### Post by Johnny3 on 2007-10-02
Did you try Synaptic Package Manager Edit Fix broken packages?
Thanks Johnny3
Gainesville Fl

---

### Post by beanco on 2007-10-02
> **Johnny3 said:**
> Did you try Synaptic Package Manager Edit Fix broken packages?
Thanks Johnny3
Gainesville Fl

sorry but I am not quite sure that is!!! 

robi

---

### Post by Zer0Nin3r on 2007-10-03
Without removing anything I was able to get synaptic back up and running by issuing the command

```
sudo aptitude update
```

Hope this helps someone.

---

### Post by beanco on 2007-10-03
now it is happening in firefirefox!!!

It does not launch and gives me the segmentaiton fault, core dumped error msg.


robi

---

### Post by Martje_001 on 2007-10-03
Do you use 7.04 or 7.10?

---

### Post by beanco on 2007-10-03
7.04

---

### Post by Ocxic on 2007-11-23
the rm -r /var/cache/apt/* worked for me

---

### Post by telic on 2007-12-06
> **Ocxic said:**
> the rm -r /var/cache/apt/* worked for me

I found that to be overkill, as it recursively erases everything in that directory, including needed sub-directories, resulting in the following error...

> E:Archive directory /var/cache/apt/archives/partial is missing.

To fix this error make sure you recreate the archives folder as well as the partial folder. open a console window and type

1. **cd /var/cache/apt**

2. Type **ls** check to make sure archives folder is displayed in case you dont see the archives folder create the folder

 **sudo mkdir archives** if you already have the archives folder then skip this step.

3. type **cd archives** , create the partial folder by typing **sudo mkdir partial**

4.   type **sudo apt-get autoclean** to make sure apt is working properly.

[http://liltux.wordpress.com/2007/06/15/howto-fix-e-archive-directory-varcacheaptarchivespartial-is-missing-error/](http://liltux.wordpress.com/2007/06/15/howto-fix-e-archive-directory-varcacheaptarchivespartial-is-missing-error/)

---

### Post by RGthundRclap on 2008-03-18
I got the same problem
the last program i installed was Opera too.

how could u fix that??

---

### Post by RGthundRclap on 2008-03-18
ohm, ok.. i know ;)   

**sudo aptitude update** that was all ;)

---

