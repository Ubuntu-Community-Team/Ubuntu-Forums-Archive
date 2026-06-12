---
title: "Openbox Menu"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by gnama on 2007-01-19
Ok so I finally got openbox working, the only LAST problem (I hope) is that I don't know how to open the menu. I can open and change what workspace I am on, but thats it, I opened the menu once but I didn't know how.:frown:

---

### Post by moore.bryan on 2007-02-02
[I]you need to make sure you've installed "menu" and i suggest "obmenu" too.
```
(sudo aptitude install --with-recommends menu obmenu)
```[/I]

---

### Post by fuscia on 2007-02-06
you can get obmenu here - [http://obmenu.sourceforge.net/](http://obmenu.sourceforge.net/)  

you'll also need to copy /etc/xdg/openbox/menu.xml to .config/openbox in your home folder. 

once this is all done, just enter *obmenu* in a terminal and you'll be all set. the menu will be accessable by right-clicking on your desktop. getting obmenu setup is a minor pain in the butt, but using it is drunken idiot simple.

---

