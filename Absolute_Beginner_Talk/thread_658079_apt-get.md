---
title: "apt-get"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by uncle hammy on 2008-01-04
This may seem like a very basic question, but I need to ask it anyways...

Searching through the posts, I always see experienced users answer with something along the lines of "Just apt-get install xyz".

My question is, how does one find out what is available to apt-get install out there, and then what exactly it is?

Thanks

---

### Post by PmDematagoda on 2008-01-04
A very easy way of doing what you want to do is using Synaptic(Ubuntu) or using Adept(Kubuntu).

---

### Post by llamakc on 2008-01-04
> **uncle hammy said:**
> This may seem like a very basic question, but I need to ask it anyways...

Searching through the posts, I always see experienced users answer with something along the lines of "Just apt-get install xyz".

My question is, how does one find out what is available to apt-get install out there, and then what exactly it is?

Thanks

You use 'search' like this:

```

apt-cache search foo

```

and any package matching 'foo' will be output on the screen with a short description. If you want to refine your search more, you can pipe the output to grep and lessen the results like this:

```

apt-cache search foo | grep bar

```

In that second example I searched for packages named foo, and limited the results to ones that also included "bar". 

Does this make sense? Open a terminal and start searching for packages. For example, do this:

```

ken@llamakc 08:42:04:~$ apt-cache search mpg321
bongo - flexible and usable media player for Emacs
cplay - A front-end for various audio players
gqmpeg - a GTK+ front end to mpg321/mpg123 and ogg123
irmp3 - A Multimedia Audio Jukebox application
mpg321 - A Free command-line mp3 player, compatible with mpg123
mserv - local centralised multiuser music server
pytone - Music jukebox with advanced features for DJs and a text-mode user interface

```

Next if you want to learn more about the package you can use another feature:

```

apt-cache show mpg321

```

Go ahead, give it a try. Also, all of these search utilities have similar GUI front ends in Synaptic/Adept.

---

### Post by Razorback on 2008-01-04
You should also update your repositories to have access to the all of the available applications.

[http://ubuntuforums.org/showthread.php?t=644478&highlight=updating+repositories](http://ubuntuforums.org/showthread.php?t=644478&highlight=updating+repositories)

---

### Post by uncle hammy on 2008-01-04
Thanks for all the prompt replies!

As far as GUI frontends, I am currently using Server edition, and trying very hard to completely setup this file server without resorting to installing X windows.

As far as the search, it makes perfect sense to me....if I have a clue what I am searching for :).  HOw do you start when you don't even know what you're looking for.  Maybe you just want to see what's out there.

---

### Post by llamakc on 2008-01-04
apt-file can be of some help:

```

 apt-cache show apt-file
Package: apt-file
Priority: optional
Section: universe/base
Installed-Size: 100
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Sebastien J. Gross <sjg@debian.org>
Architecture: all
Version: 2.0.8.2ubuntu2
Depends: perl, wget | curl, gzip (>= 1.2.4), libconfig-file-perl, libapt-pkg-perl
Suggests: ssh, sudo
Filename: pool/universe/a/apt-file/apt-file_2.0.8.2ubuntu2_all.deb
Size: 13628
MD5sum: 99a1d13ce316af33eca38cca963a717d
SHA1: 9cbc429eb600a1e478f2cac558cad82d75c38f0c
SHA256: 255d885b404501286b63e7d60519b4db7adf720b751c19a9dea1807fb712fe5a
Description: APT package searching utility -- command-line interface
 [B]apt-file is a command line tool for searching packages for the APT
 packaging system.
 .
 Unlike apt-cache, you can search in which package a file is included
 or list the contents of a package without installing or fetching it.
 .[/B]
 Please read README file for curl or wget instructions.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```Or you can point a text browser from the command line to [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by hyper_ch on 2008-01-04
> **uncle hammy said:**
> HOw do you start when you don't even know what you're looking for.  Maybe you just want to see what's out there.
When you don't know what you're looking for you have other problems.

Wanna have an email client?

```

apt-cache search email

```

this will also provide MTAs and pop3/imap servers... but when you are looking for something you should at least know a bigger category for it.... you may not know the program's name but the according group...

```

apt-cache search graphic

```

or

```

apt-cache search image

```

but they will provied too much info... so you could use:

```

apt-cache search image > output.txt

```

Then

```

nano output.txt

```

to simply "enjoy" that long list ;)

---

### Post by dreadlord_chris on 2008-01-04
For your perusal I present [Wajig]("http://linux.togaware.com/survivor/wajig.html")

"History: Motivations For Wajig	     


If you've tried to remember all the different commands to get different information about different aspects of Debian package management and then used other commands to install and remove packages then you'll know that it can become a little too much. 

Swapping between dselect, deity, deity-gtk, aptitude, apt-get, dpkg, gnome-apt, apt-cache, and so on is interesting but cumbersome. Plus personally I find dselect, deity, and aptitude confusing and even though I've spent hours understanding each of them, I don't think the time was particularly well spent. 

This Python script simply collects together what I have learnt over the years about various commands! Clearly I have yet to learn all there is."

```
sudo apt-get install wajig
```

could be the last time you type *apt-**...

---

