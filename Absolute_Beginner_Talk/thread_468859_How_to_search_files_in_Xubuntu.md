---
title: "How to search files in Xubuntu"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by broshe on 2007-06-09
Using the Xfce desktop (in Xubuntu 7.04), how can I find where some file is located ?
For example, if I want to file a file named myfile.doc
Can I somehow search for myfile.* ?
Is there some internal search engine like in windows ?

Thanks
Eli

---

### Post by ugm6hr on 2007-06-09
> **broshe said:**
> Using the Xfce desktop (in Xubuntu 7.04)... Is there some internal search engine like in windows ?


In short - No.

But there are easy solutions:
[http://ubuntuforums.org/showthread.php?t=214059](http://ubuntuforums.org/showthread.php?t=214059)

I personally used the suggestion to install GNOME Search Tool, but Catfish is supposed to be a lot lighter on resources.  Because Catfish uses *find* or *locate* you have to put a *** at the beginning and end for wildcard searches.

Terminal can find files directly e.g:
*find / -name myfile.**
or
*find /home -name *myfile**

---

### Post by Kobalt on 2007-06-09
You can use the native file browser of Xubuntu (Thunar) and a simple bash script to do this. See [here]("http://ubuntuforums.org/showthread.php?t=214059") how.

---

### Post by moore.bryan on 2007-06-09
[I]using xfce, you probably are trying to keep things low-resource, so i'd suggest going into terminal and typing
```
whereis myfile.doc
```
all of the other search tools take-up resources... but i find gnome-search-tool usable.
[/I]

---

### Post by moore.bryan on 2007-06-09
*delete my suggestion of gnome-search-tool in my last post... i just tried catfish and i'm hooked (pun intended).*

---

### Post by broshe on 2007-06-09
Thanks very much for the CatFish advice.
It works very very nicely.




> **moore.bryan said:**
> *delete my suggestion of gnome-search-tool in my last post... i just tried catfish and i'm hooked (pun intended).*

---

