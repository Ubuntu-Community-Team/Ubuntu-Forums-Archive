---
title: "setenv : command not found"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-14
I am trying to run a csh srcipt , but it fails and says that setenv and unsetenv command not found .

---

### Post by taurus on 2006-12-14
How did you run it?  Remember, the default shell is /bin/bash, not /bin/csh...

---

### Post by lance_klusener on 2006-12-14
I cd'ed to the direcotry where the script was located and tried executing it directly from there .

---

### Post by taurus on 2006-12-14
Maybe the script is meant to be running from C shell environment!  I guess that's why you post another thread about your login shell...

---

### Post by Bachstelze on 2006-12-14
Bash doesn't use setenv/unsetenv to set environment variables, it uses export/unset. So either rewrite your script for Bash or get csh.

---

### Post by lance_klusener on 2006-12-14
The script is not writeen by me , it comes with the installation package of one of the softwares that i am trying to install . 

I looked at the script and i can see setenv and unsetenv commands ( this clearly means that we cannot use bash sheel  to run the script ) .

So i need to get  the csh thing . How do i do it 

I have already tried searching for the CSH package using snyaptic and i have tried 
"apt-get install csh" . both of them have not worked

---

### Post by taurus on 2006-12-14
I already told you how to change shell in the other thread!!!

```
chsh
```

---

### Post by lance_klusener on 2006-12-14
I cannot cahnge my bourne shell to csh since csh is not installed into my ubuntu machine

---

### Post by Bachstelze on 2006-12-14
The csh package is in Universe, be sure you have it enabled and you wil be able to install it via apt-get/synaptic.
If you have it installed, you can either run it manually with the comand *bsd-csh* then run your script and *exit* to go back to Bash or make it your default shell with

```
chsh -s /bin/bsd-csh
```

---

### Post by taurus on 2006-12-14
```
sudo aptitude update
sudo aptitude install csh
```

---

### Post by lance_klusener on 2006-12-14
Hurrah !! :)  it did work . Let me change the default shell and see what happens 

Thanks

---

### Post by lance_klusener on 2006-12-14
after i did "chsh" it is asking me for a new value for the shell . I checked in the /bin direcotry . There is no csh file . So i dont know the location to feed in the chsh command

---

### Post by Bachstelze on 2006-12-14
> **HymnToLife said:**
> The csh package is in Universe, be sure you have it enabled and you wil be able to install it via apt-get/synaptic.
If you have it installed, you can either run it manually with the comand *bsd-csh* then run your script and *exit* to go back to Bash or make it your default shell with

```
chsh -s /bin/bsd-csh
```

You could also have found the executable filename from [here](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=csh&version=edgy&arch=i386) but I wouldn't recoment setting csh as your default shell, just run it, execute your script and *exit* back to Bash.

---

### Post by lance_klusener on 2006-12-14
There is no package named as bsd-csh

---

### Post by Bachstelze on 2006-12-14
Read more carefully ;) The name of the package is *csh* but the executable is */bin/bsd-csh*.

---

### Post by lance_klusener on 2006-12-14
I think the CSH package never got installed into my ubuntu machine . when i looked more carefully at the response of sudo aptitude install csh i saw that it was unable to locate the package csh . 

So i want to know where am i going wrong with installing the csh package

---

### Post by Bachstelze on 2006-12-14
As I told you, it's in Universe, make sure you have it enabled. If you don't know how to do it, [this](https://wiki.ubuntu.com/AddingRepositoriesHowto) will help you.

---

### Post by lance_klusener on 2006-12-14
No the method doesnt work with 6.10 . The GUI has changed a lot . But still i tried the link 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) drapper-commercial main 

It says the link doesnt work and might have been upgraded

---

### Post by Bachstelze on 2006-12-14
It's not the correct line, do this :

Open your sources.list :

```
sudo nano /etc/apt/sources.list
```

Spot any line with the word 'universe' and an URL in it. There should be 4 of them, each with a # before - if not, pastebin the file and we'll tell you what to add -, remove the # on all of them. Then save your file (Ctrl+O, Enter to confirm) and exit nano (Ctrl+X). Then update the packages list :

```
sudo apt-get update
```

install csh :

```
sudo apt-get install csh
```

run it :

```
bsd-csh
```

execute your script and then go back to Bash :

```
exit
```

---

### Post by lance_klusener on 2006-12-14
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


This is my source.list file 

Thanks a lot

---

### Post by Bachstelze on 2006-12-14
Delete the cdrom line and uncomment those four lines (that is, remove the '# ' so they look like this :

```
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe
```

then *sudo apt-get update*, etc.

---

### Post by lance_klusener on 2006-12-14
Thanks sir it did work , csh is finally installed and now i will reset my default shell to CSH instead of bourne

---

