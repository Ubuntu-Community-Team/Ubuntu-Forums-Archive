---
title: "NSIS Error when installing FileZilla"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Contrid on 2007-01-19
Hi there,

I have a Filezilla .exe file.
When I run this file with Wine, I get the following error :

[[IMG]http://img251.imageshack.us/img251/8959/screenshothw7.th.png[/IMG]]("http://img251.imageshack.us/my.php?image=screenshothw7.png")

Does anyone know what this means?
I'll appreciate all your comments. I'm totally confused by this. ](*,)

---

### Post by %hMa@?b&lt;C on 2007-01-19
> **Contrid said:**
> Hi there,

I have a Filezilla .exe file.
When I run this file with Wine, I get the following error :

[[IMG]http://img251.imageshack.us/img251/8959/screenshothw7.th.png[/IMG]]("http://img251.imageshack.us/my.php?image=screenshothw7.png")

Does anyone know what this means?
I'll appreciate all your comments. I'm totally confused by this. ](*,)
Filezilla has a linux version
[http://linuxappfinder.com/package/filezilla](http://linuxappfinder.com/package/filezilla)

---

### Post by Contrid on 2007-01-19
> **jeffc313 said:**
> Filezilla has a linux version
[http://linuxappfinder.com/package/filezilla](http://linuxappfinder.com/package/filezilla)

Thank you very much!!!
I was searching for that, but honestly couldn't find it.

---

### Post by Contrid on 2007-01-19
The '.deb' package is giving me another error.

> 
Error : Dependancy is not satisfiable : libc6


What could this be ?

---

### Post by %hMa@?b&lt;C on 2007-01-19
> **Contrid said:**
> The '.deb' package is giving me another error.



What could this be ?
sudo aptitude install libc6
then try installing the package

---

### Post by Contrid on 2007-01-19
> **jeffc313 said:**
> sudo aptitude install libc6
then try installing the package

Seems like it's already isntalled :

> 
contrid@contridi:~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
The following packages were automatically installed and are no longer required:
  libnl1-pre6 network-manager libnm-util0 dhcdbd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.


Hmmm...

---

### Post by %hMa@?b&lt;C on 2007-01-19
> **Contrid said:**
> Seems like it's already isntalled :



Hmmm...
is there a repo for filezilla, also, which .deb package didi you use, sid, etch or fiesty?

---

### Post by Contrid on 2007-01-19
> **jeffc313 said:**
> is there a repo for filezilla, also, which .deb package didi you use, sid, etch or fiesty?

Hi there,
I used "fiesty"
Maybe I should try the others.
What do you think?

---

### Post by %hMa@?b&lt;C on 2007-01-19
> **Contrid said:**
> Hi there,
I used "fiesty"
Maybe I should try the others.
What do you think?
i would try "etch" i think etch packages usually work with edgy (for example cinelerra i use the etch repos)

---

### Post by Contrid on 2007-01-19
> **jeffc313 said:**
> i would try "etch" i think etch packages usually work with edgy (for example cinelerra i use the etch repos)

I just tried all three.
I get the same error as before, just not "libc6" but "filezilla-common"
Guess it's my bad luck

---

