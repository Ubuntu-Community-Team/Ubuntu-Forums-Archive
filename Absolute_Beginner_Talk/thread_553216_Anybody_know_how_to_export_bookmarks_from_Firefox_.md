---
title: "Anybody know how to export bookmarks from Firefox to Epiphany?"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-09-17
Anybody know how to export bookmarks from Firefox to Epiphany?
I'm testing Debian and it uses Epiphany which is a quick web browser when you don't need PDF, Java plugins when surfing around.  So I'd like to continue using Epiphany whenever I boot into Debian instead of my Ubuntu partition.

How do I export my FF bookmarks to Epiphany?   
AND / OR how do I install Opera in Debian I can't find it when doing these commands.
```
apt-cache search opera | more
apt-cache search browser | more
apt-cache search web | more
```

---

### Post by raul_ on 2007-09-17
I don't remember but i think there is an option in Firefox that allows you to export bookmarks in different formats, and Epiphany recognizes one of them...I know because i used those browser a lot. I don't know about Opera though. Isn't there an installer in their site?

---

### Post by por100pre1 on 2007-09-17
Replace the bookmarks.html in your~/.gnome2/epiphany/mozilla/epiphany/ with the bookmarks.html from your firefox profile.

---

### Post by kerry_s on 2007-09-17
> **jingo811 said:**
> Anybody know how to export bookmarks from Firefox to Epiphany?
I'm testing Debian and it uses Epiphany which is a quick web browser when you don't need PDF, Java plugins when surfing around.  So I'd like to continue using Epiphany whenever I boot into Debian instead of my Ubuntu partition.

How do I export my FF bookmarks to Epiphany?   
AND / OR how do I install Opera in Debian I can't find it when doing these commands.
```
apt-cache search opera | more
apt-cache search browser | more
apt-cache search web | more
```


1. export it from firefox first, them import with epiphany book mark manager
2. my sources.list->

```

deb http://ftp.debian.org/debian/ etch main contrib non-free 
deb http://ftp.debian.org/debian/ lenny main contrib non-free 
deb http://www.debian-multimedia.org/ lenny main 

# su
# gpg --keyserver subkeys.pgp.net --recv-key 6A423791
# gpg --armor --export  6A423791| apt-key add -
deb http://deb.opera.com/opera/ lenny non-free 
deb http://deb.opera.com/opera-beta/ testing non-free  

deb http://security.debian.org/ etch/updates main contrib non-free 
deb http://security.debian.org/ lenny/updates main contrib non-free 

# deb-src http://ftp.debian.org/debian/ etch main contrib non-free 
# deb-src http://security.debian.org/ etch/updates main contrib non-free 
# deb-src http://ftp.debian.org/debian/ lenny main contrib non-free 
# deb-src http://security.debian.org/ lenny/updates main contrib non-free 


```

---

### Post by jingo811 on 2007-09-17
tnx will try them at school tomorrow.

---

### Post by PhrankDaChickenGeek on 2007-09-17
Epiphany has this option built in (Ubuntu 7.04) 

In epiphany, go to "Bookmarks -> Edit Bookmarks" then
"File -> Import Bookmarks...." And choose Firefox

---

### Post by jingo811 on 2007-09-18
I've always made manual backups of my bookmarks every month which saves as My_bookmarks_Sept.html
When I try to open such file with Epiphany with the Firefox import properties it doesn't recongnize and see that file.
When I use show All files and choose that *.html file it says it doesn't recognize the format.




> Replace the bookmarks.html in your~/.gnome2/epiphany/mozilla/epiphany/ with the bookmarks.html from your firefox profile.

I exported some bookmarks from Epiphany to find it's default bookmark.html I couldn't find any it seems like it uses SomeBookmark.xml , SomeBookmark.rdf or something.
```

mike@clinton:~/.gnome2/epiphany/mozilla/epiphany$ ls -la
total 92
drwx------ 3 mike mike  4096 2007-09-18 08:56 .
drwx------ 3 mike mike  4096 2007-09-17 13:42 ..
drwxr-xr-x 2 mike mike  4096 2007-09-18 08:56 Cache
-rw------- 1 mike mike 65536 2007-09-17 15:06 cert8.db
-rw------- 1 mike mike  1518 2007-09-18 08:56 cookies.txt
-rw------- 1 mike mike 16384 2007-09-17 15:06 key3.db
lrwxrwxrwx 1 mike mike    15 2007-09-18 08:51 lock -> 127.0.1.1:+3031
-rw-r--r-- 1 mike mike     0 2007-09-18 08:51 .parentlock
-rw------- 1 mike mike  6838 2007-09-17 15:06 prefs.js
-rw------- 1 mike mike 16384 2007-09-17 13:48 secmod.db
mike@clinton:~/.gnome2/epiphany/mozilla/epiphany$
```


```
mike@clinton:~/.gnome2/epiphany$ ls -la
total 88
drwxr-x--- 4 mike mike  4096 2007-09-18 09:06 .
drwx------ 9 mike mike  4096 2007-09-17 14:05 ..
-rw-r--r-- 1 mike mike  2173 2007-09-18 08:53 bookmarks.rdf
-rw-r--r-- 1 mike mike  3028 2007-09-18 08:53 ephy-bookmarks.xml
-rw-r--r-- 1 mike mike  1667 2007-09-18 09:01 ephy-favicon-cache.xml
-rw-r--r-- 1 mike mike 46640 2007-09-18 09:06 ephy-history.xml
-rw-r--r-- 1 mike mike   624 2007-09-18 08:51 epiphany-toolbars-3.xml
drwxr-x--- 2 mike mike  4096 2007-09-17 14:36 favicon_cache
drwx------ 3 mike mike  4096 2007-09-17 13:42 mozilla
-rw-r--r-- 1 mike mike   392 2007-09-18 09:06 session_crashed.xml
-rw-r--r-- 1 mike mike  2111 2007-09-17 15:06 states.xml
mike@clinton:~/.gnome2/epiphany$
```

---

### Post by jingo811 on 2007-09-18
Never mind Debian had a built in browser that supports Firefox importing much better
**Iceweasel**
So I don't have to bother with the complicated Epiphany mess and installing Opera.  Tnx for your time.

---

### Post by kerry_s on 2007-09-18
> **jingo811 said:**
> Never mind Debian had a built in browser that supports Firefox importing much better
**Iceweasel**
So I don't have to bother with the complicated Epiphany mess and installing Opera.  Tnx for your time.

iceweasel is firefox, just a different name and icon.
make sure you have synaptic, it makes installing and removing things easier.

[B]su
apt-get install synaptic[/B]

---

