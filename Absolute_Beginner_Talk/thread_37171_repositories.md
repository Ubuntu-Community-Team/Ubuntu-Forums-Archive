---
title: "repositories"
date: 2005-05-26
forum: Absolute Beginner Talk
---

### Post by odin on 2005-05-26
can anyone tell me what repositories are the best for etc/apt/sources.list?

are the ones I have by default when installing the system good enough?

I have installed ubuntu warty, can i use the hoary repositorys?

and one last question,should i migrate(change) to hoary?

---

### Post by fdoving on 2005-05-26
[QUOTE=odin]can anyone tell me what repositories are the best for etc/apt/sources.list?

are the ones I have by default when installing the system good enough?

I have installed ubuntu warty, can i use the hoary repositorys?

and one last question,should i migrate(change) to hoary?[/QUOTE]
 Hi.

Take a look at [http://ubuntuguide.org](http://ubuntuguide.org) they have a good sources.list example.

adding the hoary sources and do 'apt-get update' and 'apt-get -u dist-upgrade' will upgrade your system to hoary.

- Frode

---

### Post by odin on 2005-05-26
Thank u very much.  :grin:

---

### Post by poofyhairguy on 2005-05-27
Dont copy the three lines from the guide that say "marillat." Those can mess up your system. The rest work fine.

---

### Post by Sionide on 2005-05-27
[http://www.ubuntulinux.org/wiki/UbuntuHowCome](http://www.ubuntulinux.org/wiki/UbuntuHowCome)

This page has the scoures.list file to include Universe, Multiverse and Backports - those are the three main ones.

---

### Post by odin on 2005-08-01
I tried to add deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) ............. to my sources.list and when try apt-get update I get a "autorization required" message in those.

Can anyone explain me why?

Thank's O:)

---

### Post by poofyhairguy on 2005-08-01
[QUOTE=odin]I tried to add deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) ............. to my sources.list and when try apt-get update I get a "autorization required" message in those.

Can anyone explain me why?

Thank's O:)[/QUOTE]

Because the backports is not official and authorized yet. But it is stable and we all use it (aka ignore the warning).

---

