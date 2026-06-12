---
title: "help in installing VLC...got error.."
date: 2005-09-23
forum: Absolute Beginner Talk
---

### Post by listen on 2005-09-23
i had the following error msg when installing vlc thru "sudo apt-get....

mark@mark:~$ sudo apt-get install vlc
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
  vlc: Depends: dbus-1 (>= 0.23.4) but it is not going to be installed
       Depends: libhal0 (>= 0.4.0) but it is not going to be installed
E: Broken packages
mark@mark:~$


any ideas what's going on???


thanx in advance...

---

### Post by mlomker on 2005-09-23
> The following packages have unmet dependencies:
 

Do you have any non-ubuntu repositories in your list?  Comment them out in /etc/apt/sources.list, do an **apt-get update** and then try installing your package again.

---

### Post by listen on 2005-09-24
thank you mlomker,

i dont which ones are the non-ubuntu repositories...
below is a copy of the file, can u tell me which one to comment out...?
actually i did the apt-get upgrade b4 i tried the sudo get command...
but looking at the error again and the error when i tried to install another program using synaptic, could it be due to something called "dependencies" are they the same problem?...i will checkout on this shortly and try to find out more info..



deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary main restricted universe multiverse
deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary-updates main restricted
deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary-updates main restricted

deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary-security main restricted
deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

#backup Mirror - FAST
deb [ftp://ftp2.caliu.info/backports](ftp://ftp2.caliu.info/backports) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports](ftp://ftp2.caliu.info/backports) hoary-extras main universe multiverse restricted

---

### Post by listen on 2005-09-24
got it resolved somehow.... by changing the sources.list file  and updateing sudo apt-get.

but i still dont quite understand why there were some repositories where i have to use hoary instead of breezy to prevent errors....i will post this in a seperate thread.

thank you..

---

### Post by mlomker on 2005-09-24
Try putting a **#** in front of the last two.  They are usually the problem.  I really only recommend having backports enabled long enough to install something that you need from there and then turn them off again.

If you're running Breezy then you shouldn't need the Hoary repos from Ubuntu.  You might have to specify Hoary when using some 3rd party repositories.

---

### Post by fordfan753 on 2005-09-24
[QUOTE=listen]got it resolved somehow.... by changing the sources.list file  and updateing sudo apt-get.

but i still dont quite understand why there were some repositories where i have to use hoary instead of breezy to prevent errors....i will post this in a seperate thread.

thank you..[/QUOTE]

Breezy does not have backports repositories, so that is why it will create errors when you change the hoary packports to breezy - because they don't exist.

As mlomker pointed out, you should comment out the backports, they do cause problems.

---

### Post by listen on 2005-09-24
ok ...i get it ...thank you so much..

---

