---
title: "Need help installing Exaile!"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Europa2010AD on 2007-04-07
I run into this problem when I tried to install Exaile according to its website ([http://www.exaile.org/trac/wiki/Releases]("http://www.exaile.org/trac/wiki/Releases"))

```
$ sudo apt-get install exaile
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  exaile: Depends: python-pyvorbis but it is not going to be installed
          Depends: python-mutagen but it is not going to be installed
          Depends: python-pysqlite2 but it is not going to be installed
          Depends: python-elementtree but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Any help would be much appreciated!

---

### Post by dbbolton on 2007-04-07
the easiest way to install exaile is to install [this package]("http://www.exaile.org/files/exaile_0.2.9_i386edgy.deb") with gdebi package installer.

---

### Post by diatribe on 2007-04-07
type:

sudo apt-get -f install

then

sudo apt-get install exaile

---

### Post by Europa2010AD on 2007-04-07
> **diatribe said:**
> type:

sudo apt-get -f install

then

sudo apt-get install exaile

Your instruction seems to be working, as I no longer see the error message from earlier. However, I get this message

```
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 624kB/671kB of archives.
After unpacking 3498kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)'
in the drive '/cdrom/' and press enter
```

I Ctrl+C out of the process because I'm not sure if this is normal. Do I have to put my Ubuntu CD into the drive?

Thanks a lot for the help!

---

### Post by igknighted on 2007-04-07
You have listed you CD as a repo source for some reason (if you installed with the alt. CD this is normal).  You should go into synaptic or the sources.list file and comment it out or remove it completely.

---

### Post by Europa2010AD on 2007-04-07
> **igknighted said:**
> You have listed you CD as a repo source for some reason (if you installed with the alt. CD this is normal).  You should go into synaptic or the sources.list file and comment it out or remove it completely.

Yes, I did indeed install from the alt. CD.  I edited the sources.list file like you said, and it installed perfectly!

Much thanks to everyone who answered the post! :)

---

