---
title: "how to remove un-needed update"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by oilchangeguy on 2007-03-14
this computer does not have a dvd drive. and one of the recent 6.06 updates includes new dvd burner software. my question is, how do i stop this update from being included in the available updates list?

---

### Post by bapoumba on 2007-03-14
Could you give the package name ? My guess is that it's part of ubuntu-desktop (or kubuntu- or xubuntu- depending on what ubuntu flavor you installed), and it is tied in the distribution via its dependency. Would it be an issue for you to just keep it ?

---

### Post by eljalill on 2007-03-14
if you uninstall (best: remove completely) the program this is a update for in synaptics,  you will stop getting updates. 

You could also use apt-get remove (--purge) , but I am personally more comfortable with synaptics...

---

### Post by eljalill on 2007-03-14
Oh sorry, I guess bapoumba posted, when I was still typing..
Of course you would first want to check, that you can actually remove it!

( I just hope, that the fact, that you didn't answer does not mean you removed it, wrecked your system, and can't get online now.... But I guess it doesn't ;) )

---

