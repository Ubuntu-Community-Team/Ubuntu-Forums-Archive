---
title: "apt-get == aptitude, whats the diffrence ???"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2007-01-06
Why are there two commands that do the same thing ? Or am i wrong ?

---

### Post by CroEragon on 2007-01-06
That's two different command line package managers.

---

### Post by Sasa_Ivanovic on 2007-01-06
diffrent by what ? name ?

---

### Post by CroEragon on 2007-01-06
I don't know exactly but i think that apt-get handles dependencies better but im not sure.

---

### Post by Sasa_Ivanovic on 2007-01-06
I'm about to reinstall Ubuntu, and i don't want to download all the packagaes again. Where can i find them, and what should i do to back them up.

---

### Post by meborc on 2007-01-06
aptitude is newer... and it is recomended to use it if you need to uninstall packages afterwards... for example, if you want to try out kubuntu-desktop and afterwards get your ubuntu back as it was, then using apt-get you would need to uninstall all packages "by hand" but using aptitude, it will remember all the packages the meta-package needed and it will uninstall also all...

or smth like that ;)

i still use apt-get as i'm used to it :mrgreen:

---

### Post by CroEragon on 2007-01-06
What do you wanna do?
Do you have to reinstall because some other reason or you want fresh installation. If you want same installation after reinstall you can use partimage. After you restore Ubuntu will be same as before reinstalling.
Google partimage for more informations.

---

### Post by Sasa_Ivanovic on 2007-01-06
some other reason ...

where are those packages located, and how are they called ?
and also when i install Ubuntu should i change some files in order make Ubuntu aware of em ?

---

### Post by CroEragon on 2007-01-06
partimage is not Ubuntu package, it is liveCD.
With it you make exact image of drive and then you restore it after reinstallation. Similar to .iso cd image but hard drive image

---

### Post by Sasa_Ivanovic on 2007-01-06
I've got a Ubuntu 6.10 that's acting like a Live CD and at the same time you can install Ubuntu from it. Would this CD do ?
And how should i do that ?
Is it complicated ?

---

### Post by NoWhereMan on 2007-01-06
usually the packages you downloaded are all in /var/cache/apt (IIRC) (unless you did an apt-get autoclean which would delete them all)

---

### Post by quartzy on 2007-01-06
The packages are located in /var/cache/apt/ (well archives) but if you want to keep them zip that whole folder then put it back in the same place and it should find them.. 

I would assume its the same for aptitiude but don't know for sure..

---

### Post by Sasa_Ivanovic on 2007-01-06
forget it !
just tell me where are those files located ...
i can't fix the problem with that.

---

### Post by Sasa_Ivanovic on 2007-01-06
ok, found them. Thanks everyone !

---

