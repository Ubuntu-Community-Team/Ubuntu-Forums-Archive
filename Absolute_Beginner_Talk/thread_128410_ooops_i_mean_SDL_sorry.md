---
title: "ooops i mean SDL sorry"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by firefly123 on 2006-02-11
when i run ./configure bebore prompt i get

checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.0 not found!
firefly123 is online now   	Reply With Quote

---

### Post by Lord Illidan on 2006-02-11
> when i run ./configure bebore prompt i get

checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.0 not found!
firefly123 is online now       Reply With Quote 
First: Use a better thread title : oops i mean SDL sorry just doesn't cut it.

Second:

What are you trying to install?

Third:

Have you installed the sdl development libs through synaptic?

---

### Post by firefly123 on 2006-02-11
[QUOTE=Lord Illidan]First: Use a better thread title : oops i mean SDL sorry just doesn't cut it.

Second:

What are you trying to install?
Have tried 6 diffrent programs and games same error

Third:

Have you installed the sdl development libs through synaptic?[/QUOTE]

cant find above package even with a search

---

### Post by Lord Illidan on 2006-02-11
Have you enabled the extra repos?

Give us your /etc/apt/sources.list

It should look like this :
```

deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse
```

EDIT : You might want to see this link : [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by jimrz on 2006-02-11
packages are there in synaptic...you must need to add repositories....do you have universe/multiverse enabled?

EDIT:  ooops... Lord I too quick for me

---

### Post by firefly123 on 2006-02-11
here is my list

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) breezy universe multiverse main restricted


Have refreshed the list and still cant find it

what is it called and what section is it in

cheers

or am i missing something

---

### Post by firefly123 on 2006-02-11
hi
never found sdl but got it as a rpm at the sdl site

---

### Post by cwaldbieser on 2006-02-11
[QUOTE=firefly123]hi
never found sdl but got it as a rpm at the sdl site[/QUOTE]
Not sure what you are searching for, but try "libsdl".  You can even search from the terminal like this:
```

$ apt-cache search libsdl

```

---

