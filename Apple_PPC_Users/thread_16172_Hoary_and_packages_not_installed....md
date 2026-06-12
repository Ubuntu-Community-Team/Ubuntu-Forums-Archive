---
title: "Hoary and packages not installed..."
date: 2005-02-19
forum: Apple PPC Users
---

### Post by melchior on 2005-02-19
i'm not sure this is the right place to be posting this, possibly the hoary forum is more appropriate but then again it may be ppc specific... 

i downloaded [http://mirror.pacific.net.au/linux/ubuntu-cd/daily/20050215.4/hoary-install-powerpc.iso](http://mirror.pacific.net.au/linux/ubuntu-cd/daily/20050215.4/hoary-install-powerpc.iso) overnight and set to installing it on my ibook dual usb. everything was fine until, at an unknown point through the downloading and installing packages it stopped, opened aptitude and gave me a message that some packages could not be installed and trying again may solve the problem. 

i can't get it to try again because i don't know where to start. i don't know which packages should have been installed but haven't etc. not that i can get aptitude to actually download anything no matter what combination of g or + i try. 

tried 'startx' but no cigar, packages are not there. 

little help please?

---

### Post by az on 2005-02-19
Maybe the internet connection borked out...

To get things going again run:

sudo apt-get -f install

I read that Hoary will not offer the option of installing packages from the internet from the installer, regardless of security packages, until the system is up and running.  This would avoid this sort of problem.

---

