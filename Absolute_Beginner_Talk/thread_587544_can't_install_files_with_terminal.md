---
title: "can't install files with terminal"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by trynet on 2007-10-22
I just got my internet connection set up, and I'm having problems installing "wine"
I entered this into the terminal:
```
 http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb

```
and get this response back:
```
Error parsing proxy URL http://:8080/: Invalid host name.
```

so...what am I doing wrong...

---

### Post by PurposeOfReason on 2007-10-22
I don't think it's possible to enter a link to download something. You should already have GIMP by default too. . .

---

### Post by Maestro23 on 2007-10-22
1. That is a tarball for gimp.

2. Gimp comes installed in ubuntu by default. Wine is in the Ubuntu repo's as well.

3. If you want the latest versions of each, then we can go from there.

---

### Post by trynet on 2007-10-22
uhhh...whoops, wrong thing...
I fallowed a guide for setting up wine- 
 [http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb](http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb)
 and get ```
Error parsing proxy URL http://:8080/: Invalid host name.
``` *edits first post*

---

### Post by nchase on 2007-10-22
have you searched google or the forums?

here's a good link that tells you how to install the newest official wine package for ubuntu 7.10:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by trynet on 2007-10-22
yeah, I searched google and got this tutorial- [http://ubuntuforums.org/showthread.php?t=149585&highlight=wine](http://ubuntuforums.org/showthread.php?t=149585&highlight=wine)

after the first copy and paste, it gave me that error message -_-...

---

### Post by nchase on 2007-10-22
use the link i just posted

---

### Post by RomeReactor on 2007-10-22
Hi. To download that package, you can use wget from the terminal:
```
wget http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb
```
Or paste that http address in Firefox, and you'll be prompted for an action (Open, Save as, etc).

This version of Wine is newer than the one in the repositories.

---

### Post by trynet on 2007-10-22
it still gives me the error...
I'll try your link now.
edit- still I get the error...
I think ubuntu hates me -_-...

---

### Post by trynet on 2007-10-23
bump, please?
I think this OS is out to get me.

---

### Post by trynet on 2007-10-23
linux...is...out...to get me...RUN!

---

### Post by Maestro23 on 2007-10-23
> **trynet said:**
> bump, please?
I think this OS is out to get me.

Goto the following page and try getting it this way:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Just follow the instructions.

---

### Post by trynet on 2007-10-23
> **Maestro23 said:**
> Goto the following page and try getting it this way:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Just follow the instructions.

when I put in 
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
I get
```
gpg: no valid OpenPGP data found.

```

and when I try
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
```
I get
```
Error parsing proxy URL http://:8080/: Invalid host name.

```

so what the hell am I doing wrong?!!?!!?
linux is SOOOO out to get me...

---

### Post by trynet on 2007-10-23
please? is my comp screwed up, or is it me?

---

### Post by Maestro23 on 2007-10-23
> **trynet said:**
> please? is my comp screwed up, or is it me?

Are you behind a proxy by chance.  Check: System>> Prefs>> Network Proxy

If you are** not**, make sure "Direct Internet Connection" is checked.

---

### Post by trynet on 2007-10-23
where do I check direct internet connection?

edit- whoops, found it... *finds eyes*
no proxys, I disabled them a while ago.
edit #2- still same errors -_-...linux really does hate me...

---

### Post by Billy_McBong on 2007-10-23
[COLOR="Blue"]do you need the newest version of wine?
if not you can just do ```
sudo apt-get install wine
```[/COLOR]

---

