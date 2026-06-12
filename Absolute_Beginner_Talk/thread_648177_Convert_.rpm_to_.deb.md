---
title: "Convert .rpm to .deb"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by TrakerJon on 2007-12-23
1. Alien Installation

Alien is available in the normal Debian repositories, so we can install it like this:

**sudo apt-get install alien**

 
2. Converting .rpm To .deb

Next we download the current <file name>.rpm package:

**cd /tmp**

**wget http://www.website.com/downloads/community/1.1/Linux/<file name>.rpm**

To convert it into a .deb package, we simply run

**sudo alien <file name>.rpm**

Note: use the --scripts parameter to include the scripts.

Afterwards, run

**sudo ls -l**

in the /tmp directory, and you'll see that alien has created the file <file name>.deb. You'll also notice that alien has counted up the version number, it's now 1.1-2 instead of 1.1-1. If you want to keep the original version number, you must use the -k switch:

**sudo alien -k <file name>.rpm**

will create the file <file name>.deb

To install the new .deb file, we use dpkg -i:

**sudo dpkg -i <file name>.deb**

Now <file name> is installed and fully functional (you still might have to edit its configuration file though).

If you want to save the dpkg -i step, you can have alien install the package. The command

**sudo alien -i <file name>.rpm**

will convert the original rpm package and immediately install it.

You see, converting .rpm files to .deb files is very easy. You can have a look at

**man alien**

to learn about what else you can do with alien.

---

### Post by Wiebelhaus on 2007-12-23
Hella sweet , trying this out now.

---

### Post by Wiebelhaus on 2007-12-23
Works like a charm, is this safe? Cause I love it.

---

### Post by TrakerJon on 2007-12-23
Should be fairly safe...the occasional config file may have to be edited. Enjoy.

---

### Post by CodE-E on 2007-12-24
bc@Goldadler:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alien
bc@Goldadler:~$ 

:(

---

### Post by ~LoKe on 2007-12-24
It's a good thing to know, but in all honesty, for something that involved, I'd rather just compile it myself.

---

### Post by Lord DarkPat on 2007-12-24
> bc@Goldadler:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package alien
bc@Goldadler:~$ 
Try installing in Synaptic/Adept with all repos enabled. 
Good News: The drivers that are available only in RPM have a high enough success rate, but no guarantee. My grafix driver is converted from rpm. works like a charm :):guitar:

---

### Post by CodE-E on 2007-12-24
Ohh, nevermind the problem I had... I havent used Linux in a few years and forgot about the apt-get source list. I had to uncomment a bunch of sources in /etc/apt-get/sources.list and then I was able to install alien. :)

---

