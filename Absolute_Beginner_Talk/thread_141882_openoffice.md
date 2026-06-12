---
title: "openoffice"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by mwanafunzi on 2006-03-09
Hi all,
    I just downloaded openoffice 2.0.2 and I was hoping to get some help on installing it. I have unpacked the file...But all the installation files are rpms. Can I still install the program? Should I wait for it to be added in universe?

thanks

---

### Post by Brunellus on 2006-03-09
do NOT bother with RPMs.  Instead:

open a terminal and type

sudo gedit /etc/apt/sources.list

that will open a text editor with your apt sources.list in it.  at the end, copy and paste this line:

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

Then save and quit.   run Synaptic, hit refresh, and search for the packages you want to add.  

This will add a repository with contributed OOo2 .debs files, accessible by apt/synaptic.  Note that while people have reported some success with this repository, it is NOT YET OFFICIAL UBUNTU...if this bothers you, wait until Dapper Drake releases at the end of April.

---

### Post by treris on 2006-03-09
however, the repo's are still on OOo 2.0.1 instead of the 2.0.2, does anybody know when that is going to change??

I would really like to upgrade from 2.0.1 to 2.0.2 myself, but I would prefer to do it using the repo's instead of using alien to make deb's out of the rpm's

---

### Post by cyberb0b on 2006-03-09
[QUOTE=mwanafunzi]Can I still install the program?[/QUOTE]Yes, it is possible for you to do this, but... [QUOTE=mwanafunzi]Should I wait for it to be added in universe?[/QUOTE]Yes.  Yes yes.  Yes yes yes yes yes. (well, not universe, get the deb from here: [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) but still yes, just wait)

---

### Post by Sokraates on 2006-03-10
If you want some adventure, try the debs from

[ftp://ftp.linux.cz/pub/localization/OpenOffice.org/2.0.2/](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/2.0.2/)

**A word of caution: **I used this ftp a lot with Hoary and Breezy and in general it worked alright, but be ready for possible problems. These debs were not made specifically for Breezy, after all (unlike the ones on  [http://people.ubuntu.com/~doko/OOo2]("http://people.ubuntu.com/%7Edoko/OOo2")).

---

### Post by linbetwin on 2006-03-10
OpenOffice.org 2.0.2 is in Dapper. I don't think it will ever be included in the Breezy repositories.

You could change your sources.list and upgrade to Dapper,
You could install Dapper Flight 4,
You could wait for the Beta, or
You could wait for the final release.

---

