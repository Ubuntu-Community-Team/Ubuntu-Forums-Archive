---
title: "Is There a Good Linux Web Design Program?"
date: 2005-08-08
forum: Absolute Beginner Talk
---

### Post by polo_step on 2005-08-08
Just curious.  I have Dreamweaver MX on the XP box, but if there's a fairly decent Linux equivalent, I'd like to give it a try just for fun.  I don't need state-of-the-art in this case...really, just a sexy HTML editor, but a fancy program is OK too. :smile: 

Recommendations are welcome -- thanks for any help!

---

### Post by SGC on 2005-08-08
- [Quanta Plus](http://quanta.kdewebdev.org/) (apt-get install quanta)
- [Nvu](http://www.nvu.com/) (apt-get install nvu)
- [Bluefish](http://bluefish.openoffice.nl/index.html) (apt-get install bluefish)

While you can install Quanta Plus without enabling any repository, you need to enable universe repository for Bluefish and Backports repository for Nvu.

Quanta Plus is a kde-based program, so If you are using Ubuntu it will download a few other kde libraries. But its the closest thing to Dreamweaver

---

### Post by OttoDestruct on 2005-08-08
[QUOTE=SGC]- [Quanta Plus](http://quanta.kdewebdev.org/) (apt-get install quanta)
- [Nvu](http://www.nvu.com/) (apt-get install nvu)
- [Bluefish](http://bluefish.openoffice.nl/index.html) (apt-get install bluefish)

While you can install Quanta Plus without enabling any repository, you need to enable universe repository for Bluefish and Backports repository for Nvu.

Quanta Plus is a kde-based program, so If you are using Ubuntu it will download a few other kde libraries. But its the closest thing to Dreamweaver[/QUOTE]

I'm not finding nvu even with all the repositories.

---

### Post by ozzie123 on 2005-08-08
Hello, still a newbie here but are trying to help other newbie users.

Could you list what your source.list contain? I activated the backports via the tutorial in [www.ubuntuguide.org](www.ubuntuguide.org) and it works like a charm (to download Nvu that is).

---

### Post by OttoDestruct on 2005-08-08
[QUOTE=ozzie123]Hello, still a newbie here but are trying to help other newbie users.

Could you list what your source.list contain? I activated the backports via the tutorial in [www.ubuntuguide.org](www.ubuntuguide.org) and it works like a charm (to download Nvu that is).[/QUOTE]

I've been running Ubuntu for some time now, I have the repositories enabled exactly as stated in there, I've done sudo apt-get update. It's not finding the package, nor is it listed in Synaptic.

---

### Post by ozzie123 on 2005-08-08
[QUOTE=OttoDestruct]I've been running Ubuntu for some time now, I have the repositories enabled exactly as stated in there, I've done sudo apt-get update. It's not finding the package, nor is it listed in Synaptic.[/QUOTE]
 So sorry, I don't mean to offend you or anything :-).

Well, have you tried to update your source list? It's really weird because Nvu is available on my list.

---

### Post by SGC on 2005-08-08
Here is the link to the backports package:
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/nvu_0.99+1.0pre-1~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/nvu_0.99+1.0pre-1~5.04ubp1_i386.deb)

Download it and install it with:
dpkg -i nvu_0.99+1.0pre-1~5.04ubp1_i386.deb

---

### Post by OttoDestruct on 2005-08-08
[QUOTE=ozzie123]So sorry, I don't mean to offend you or anything :-).

Well, have you tried to update your source list? It's really weird because Nvu is available on my list.[/QUOTE]

Ive recopied that sources list in the guide 3 times, all with the same result. Nvu is not there.

---

### Post by ozzie123 on 2005-08-08
[QUOTE=OttoDestruct]Ive recopied that sources list in the guide 3 times, all with the same result. Nvu is not there.[/QUOTE]
 Try the solution from SGC and make sure you have updated your dpkg. :)

---

### Post by KingBahamut on 2005-08-08
Cant forget the other IDEs 

Anjuta, Gambas, Eclipse.

---

### Post by Lord Illidan on 2005-08-08
I've always used Nvu, but thanks to you, I think I will start using Quanta Plus...

> Anjuta, Gambas, Eclipse. 

Aren't these IDEs for compilers? I thought he meant web development apps.

---

### Post by KingBahamut on 2005-08-08
They are, probably slightly OT for me to mention them.

---

