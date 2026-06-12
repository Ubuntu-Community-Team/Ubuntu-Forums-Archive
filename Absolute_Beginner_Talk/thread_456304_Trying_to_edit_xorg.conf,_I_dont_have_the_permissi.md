---
title: "Trying to edit xorg.conf, I dont have the permissions"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by virgilnilson on 2007-05-27
I tried to alter the file in properties to be read and writable, but it would tell me that I am not the owner so I cannot do that. Then when just editing it in gedit and trying to save it as itself and replace it, it tells me that I do not have the permissions necessary to do so.

Also, in writing this thread I just realized that my apostrophe key does not produce any output. Not when pressed normally or with shift.

EDIT: Pressing the apostrophe key before I press the letter s produces an &#347;.

---

### Post by taurus on 2007-05-27
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by virgilnilson on 2007-05-27
gksudo gedit /etc/x11/xorg.conf
(gedit:10922): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


I then get a gedit window with a blank xorg.conf.

Trying it again produces the same blank document in gedit, but did not produce that error message.

---

### Post by Zuuswa on 2007-05-27
try 'sudo' instead of 'gksudo'

---

### Post by taurus on 2007-05-27
What exactly is the command that you typed?  What's the output of this command from a terminal?

```
ls -la /etc/X11
```

p.s.  And _please_ use gksudo, NOT sudo, when you use gedit as root.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by taurus on 2007-05-27
> **virgilnilson said:**
> gksudo gedit **/etc/[COLOR="Blue"]x[/COLOR]11/xorg.conf**
(gedit:10922): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


I then get a gedit window with a blank xorg.conf.

Trying it again produces the same blank document in gedit, but did not produce that error message.

There's your problem.  It's capital X, not x.

```
gksudo gedit /etc/[COLOR="Blue"]X[/COLOR]11/xorg.conf
```

---

### Post by virgilnilson on 2007-05-27
> **taurus said:**
> There's your problem.  It's capital X, not x.

```
gksudo gedit /etc/[COLOR="Blue"]X[/COLOR]11/xorg.conf
```

Thank you very much, that worked. =]

---

