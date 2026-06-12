---
title: "Compile error?"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-05-21
I keep getting this error when trying to compile a program from source.

```
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.0 not found!
aktiwers@ubuntu:~/stellarium-0.8.0$

```

Everything goes just fine, but at the end I get this message?

What is wrong? and what can I do?

This happends on the when I type ./configure

Thanks for any help.

---

### Post by codejunkie on 2006-05-21
[QUOTE=aktiwers]I keep getting this error when trying to compile a program from source.

```
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.0 not found!
aktiwers@ubuntu:~/stellarium-0.8.0$

```

Everything goes just fine, but at the end I get this message?

What is wrong? and what can I do?

This happends on the when I type ./configure

Thanks for any help.[/QUOTE]
try running```
sudo apt-get install libsdl1.2-dev
```in a terminal/konsole

---

### Post by aktiwers on 2006-05-21
Thanks a lot!

I did what you said and some more, please have a look:
```

** aktiwers@ubuntu:~$** sudo apt-get install libsdl1.2-dev
Password:
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
** aktiwers@ubuntu:~$ **sudo apt-get install libsdl1.2-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libartsc0-dev but it is not going to be installed
E: Broken packages
** aktiwers@ubuntu:~$** sudo apt-get install libartsc0-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libartsc0-dev: Depends: libartsc0 (= 1.4.3-0ubuntu1) but 1.5.1-0ubuntu0breezy1 is to be installed
E: Broken packages
** aktiwers@ubuntu:~$**
``` 
Now whats wrong?

Thanks for the help so fare! :KS

---

### Post by codejunkie on 2006-05-21
[QUOTE=aktiwers]Thanks a lot!

I did what you said and some more, please have a look:
```

** aktiwers@ubuntu:~$** sudo apt-get install libsdl1.2-dev
Password:
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
** aktiwers@ubuntu:~$ **sudo apt-get install libsdl1.2-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libartsc0-dev but it is not going to be installed
E: Broken packages
** aktiwers@ubuntu:~$** sudo apt-get install libartsc0-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libartsc0-dev: Depends: libartsc0 (= 1.4.3-0ubuntu1) but 1.5.1-0ubuntu0breezy1 is to be installed
E: Broken packages
** aktiwers@ubuntu:~$**
``` 
Now whats wrong?

Thanks for the help so fare! :KS[/QUOTE]
run ```
sudo gedit /etc/apt/sources.list
``` and post the file here
if your using kde try
```
sudo kate /etc/apt/sources.list
```

---

### Post by aktiwers on 2006-05-21
Here is my /ect/apt/source.list

> deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

## official backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## breezy-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH [http://ovh.com](http://ovh.com)
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## plf secundairy repo. Use if primary repo is offline.
## FTP mirror from [http://free.fr](http://free.fr) (french ISP)
## deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
## deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

## plf mirror. Use if primary and secundairy are offline
## deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## wine
## deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

## opera web browser
## deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./



# for IRSSI
#Then run apt-get update; apt-get install irssi
#deb [http://www.davidpashley.com/debian/irssi-sarge/](http://www.davidpashley.com/debian/irssi-sarge/) ./
 

# BOINC packages for Ubuntu 5.10 "Breezy Badger"
deb     [http://pkg-boinc.alioth.debian.org/ubuntu](http://pkg-boinc.alioth.debian.org/ubuntu) breezy universe
deb-src [http://pkg-boinc.alioth.debian.org/ubuntu](http://pkg-boinc.alioth.debian.org/ubuntu) breezy universe


Thanks!

---

### Post by richbarna on 2006-05-21
For stellarium, you can just :-
> sudo apt-get stellarium

If you really want the 0.8 version not the 0.7.1 version :-
Check that you have enabled all the repositories in your sources.list,
and then download libsdl1.2-dev and libartsc0-dev.

Edit: Aktiwers got there first :)
        Was just about to ask to post the sources.list

---

### Post by codejunkie on 2006-05-21
[QUOTE=aktiwers]Here is my /ect/apt/source.list



Thanks![/QUOTE]
well it looks ok you have the universe & multiverse repos enabled try running 
```
sudo apt-get update
``` then ```
sudo apt-get install libsdl1.2-dev
```
if that doesn't work try ```
sudo apt-get install libsdl-dev
```

---

### Post by aktiwers on 2006-05-21
Again this happends, and I did run the sudo apt-get update first.

```

**aktiwers@ubuntu:~$** sudo apt-get install libsdl1.2-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libartsc0-dev but it is not going to be installed
E: Broken packages
**aktiwers@ubuntu:~$** sudo apt-get install libsdl-dev
Reading package lists... Done
Building dependency tree... Done
Note, selecting libsdl1.2-dev instead of libsdl-dev
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libartsc0-dev but it is not going to be installed
E: Broken packages
[B]aktiwers@ubuntu:~$
[/B]
```

---

### Post by codejunkie on 2006-05-21
[QUOTE=aktiwers]Again this happends, and I did run the sudo apt-get update first.

```

**aktiwers@ubuntu:~$** sudo apt-get install libsdl1.2-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libartsc0-dev but it is not going to be installed
E: Broken packages
**aktiwers@ubuntu:~$** sudo apt-get install libsdl-dev
Reading package lists... Done
Building dependency tree... Done
Note, selecting libsdl1.2-dev instead of libsdl-dev
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libartsc0-dev but it is not going to be installed
E: Broken packages
[B]aktiwers@ubuntu:~$
[/B]
```[/QUOTE]
it's most likely the packages are conflicting with one of your repos, or the package or some of it's dependencies, has been removed from the repo. try this first run 
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup
```
then run ```
sudo gedit /etc/apt/sources.list
```
and paste this in there
```
deb http://archive.ubuntu.com/ubuntu/ breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ breezy universe
deb-src http://archive.ubuntu.com/ubuntu/ breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy multiverse

deb http://security.ubuntu.com/ubuntu breezy-security multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security multiverse
```
save the file and run ```
sudo apt-get update
```then try to install the package/packages if this doesn't work with the clean sources.list file, then the package or it's dependencies has been removed and there is nothing you can do except download the source files for libsdl and compile and install them first, or wait until there re added to the repo.

---

### Post by aktiwers on 2006-05-21
Thanks a lot, I will try this tomorrow!
Its getting late here (as usual) and I will have to go to bed.

I will update tomorrow.

Thanks again!

---

