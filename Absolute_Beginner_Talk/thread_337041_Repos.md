---
title: "Repos"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Riyonuk on 2007-01-12
I just stumbled upon the Ubuntu Audacious Repos, and would like if there are more repos. I'm pretty sure there are, Im just looking for Ubuntu related ones. Not like automatix, kinda scared of that program.

---

### Post by jvc26 on 2007-01-12
There is a repos list here (a link from Ubuntu guide)
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
And trevino's list:
[http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/](http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/)
And the complete sources list:
[http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html](http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html)

All links taken from:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

Hope that helps?
Il

---

### Post by Riyonuk on 2007-01-12
Are these just Edgy? And yes it helped...kinda

That audacious one I found, [http://ubuntuforums.org/showthread.php?t=308286](http://ubuntuforums.org/showthread.php?t=308286), isnt even on the lists, when I searched, I kept seeing

deb [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental audacious
deb-src [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental audacious

Which is not the same as the ubuntu link. Are they just out of date?

---

### Post by jvc26 on 2007-01-12
The official audacious ones for Ubuntu are:
```

deb http://static.audacious-media-player.org/ubuntu edgy main
deb-src http://static.audacious-media-player.org/ubuntu edgy main
**or**
deb http://static.audacious-media-player.org/ubuntu dapper main
deb-src http://static.audacious-media-player.org/ubuntu dapper main

```
The other repo links you have found may well be the ones right from the source (i.e. the ones the guys who are making it host) The ubuntu ones from that post are official for ubuntu and consequently should work with no problems.

Those other repos I found were for edgy, however you can take a peek:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)
At the bottom of that section is a bit about other sources.
Il

---

### Post by Riyonuk on 2007-01-12
Thanks it helped alot, I think Ill make my own sources list :D as I really dont have much use for those other programs. Again thanks!

---

### Post by Riyonuk on 2007-01-13
Also, the deb-src, do I really need this? Is it for users that wish to compile there own software?

---

### Post by jvc26 on 2007-01-13
No I dont think you need deb-src addresses unless you want to be able to download the source code straight from the repo.
Il

---

### Post by Riyonuk on 2007-01-13
Alright, now what about packages.ubuntu.com? Lets take conky, Im trying to get that. I have to download the conky.deb and click on each dependency link and download each of those? Is there an easier way?

[http://packages.ubuntu.com/edgy/utils/conky](http://packages.ubuntu.com/edgy/utils/conky)

---

### Post by jvc26 on 2007-01-13
can you not get it via:
```

sudo apt-get install conky

```
That would get all the dependencies for you too - is this not a possible command?
Il

---

### Post by Riyonuk on 2007-01-13
No no, I dont have internet on my home pc, Im currently at the library (in windows) trying to download some packages to use at home. Its very hard finding the dependencys.

---

