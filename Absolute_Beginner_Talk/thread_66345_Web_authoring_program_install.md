---
title: "Web authoring program install"
date: 2005-09-16
forum: Absolute Beginner Talk
---

### Post by hansoffate on 2005-09-16
So far the best "web authoring program" i have found is nvu.  
[http://www.nvu.com/](http://www.nvu.com/)

It seems like a very good and easy to use program.  Does anyone have any other suggestions?

But the real reason why i am posting is because i want to install the file which i downloaded.

i downloaded this one 
nvu-1.0-pc-linux2.6.10-gnu.tar.bz2 - Tarball built on Linspire 5.0 (Debian k2.6.10), gcc/g++ 3.3.5

Would that one work?

anyways, in console i typed and got this.

hans@hans:~/Internet_downloads$ sudo dpkg -i nvu-1.0-pc-linux2.6.10-gnu.tar.bz2 Password:
dpkg-deb: `nvu-1.0-pc-linux2.6.10-gnu.tar.bz2' is not a debian format archive
dpkg: error processing nvu-1.0-pc-linux2.6.10-gnu.tar.bz2 (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 nvu-1.0-pc-linux2.6.10-gnu.tar.bz2
hans@hans:~/Internet_downloads$

any suggestions to  what i should do?

---

### Post by tikal26 on 2005-09-16
[QUOTE=hansoffate]So far the best "web authoring program" i have found is nvu.  
[http://www.nvu.com/](http://www.nvu.com/)

It seems like a very good and easy to use program.  Does anyone have any other suggestions?

But the real reason why i am posting is because i want to install the file which i downloaded.

i downloaded this one 
nvu-1.0-pc-linux2.6.10-gnu.tar.bz2 - Tarball built on Linspire 5.0 (Debian k2.6.10), gcc/g++ 3.3.5

Would that one work?

anyways, in console i typed and got this.

hans@hans:~/Internet_downloads$ sudo dpkg -i nvu-1.0-pc-linux2.6.10-gnu.tar.bz2 Password:
dpkg-deb: `nvu-1.0-pc-linux2.6.10-gnu.tar.bz2' is not a debian format archive
dpkg: error processing nvu-1.0-pc-linux2.6.10-gnu.tar.bz2 (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 nvu-1.0-pc-linux2.6.10-gnu.tar.bz2
hans@hans:~/Internet_downloads$

any suggestions to  what i should do?[/QUOTE]
 I think that there is version in backports, but it might not be current and there is a debian package for it .

---

### Post by hansoffate on 2005-09-16
hans@hans:~$ sudo apt-get install nvu
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package nvu

i guess not?  or maybe it isn't right...

---

### Post by professor_chaos on 2005-09-16
can you post the contents of /etc/apt/sources.list

---

### Post by hansoffate on 2005-09-17
Yes sir.

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

# Dépôts normaux
deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) hoary main restricted

# Universe et Multiverse
deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) hoary universe multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) hoary universe multiverse

# Mises à jour
deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) hoary-updates main restricted

# Mises à jour de sécurité
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse

# Extra
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

# Backports officiels
#deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

# Backports non-officiels
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

# KDE 3.4.2
#deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

# PHP5
#deb [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5 hoary

# suPHP (sources)
#deb-src [http://manu.home-dn.net/debian/suphp-preview](http://manu.home-dn.net/debian/suphp-preview) sid main

# Wine
#deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) hoary/

---

### Post by aysiu on 2005-09-17
Are you French? Where did all those sources come from?

In any case, nvu is definitely [in the backports](http://i22.photobucket.com/albums/b337/psychocats/cfaa6ec5.png).

Follow the instructions here:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

But paste the extra repositories over your current repositories. That is, erase all your current repositories completely and then make the new "extra repositories" all the repositories you have. Then *sudo apt-get update* and *sudo apt-get install nvu*.

---

### Post by hansoffate on 2005-09-17
Thank you so much.  I got nvu now.  Now i just need to figure out where to save my website...considering nvu said i can't save it in /var/www/.  where i believe apache is hosting it.

---

