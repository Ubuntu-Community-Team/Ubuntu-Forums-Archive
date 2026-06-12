---
title: "Can't Update"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by shawn fernandes on 2007-01-29
I have got updates but I can't seen to update and I get this message:
A error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong. The error message was 'Error: Opening the cache (E: type 'wget' is not know on line 55 in source list /etc/apt/sources .list , E: the list of sources could not be read.)

What do I do?


Thank you.

---

### Post by bluefrog on 2007-01-29
sudo vi /etc/apt/sources.list
and correct your sources.list at line 55 apparently.

should start with deb  not wget...

James

---

### Post by mikewhatever on 2007-01-29
It looks like there is something wrong with line 55 of your sources.list.
Post the list of sources here to have a look.
gksudo gedit /etc/apt/sources.list

---

### Post by jvc26 on 2007-01-29
I have the odd feeling you have put a wget command to get a repo key into your sources.list which is consequently messing up line 55. If you can post it up here that would help :)
Il

---

