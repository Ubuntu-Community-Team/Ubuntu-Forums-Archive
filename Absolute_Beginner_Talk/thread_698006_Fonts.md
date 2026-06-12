---
title: "Fonts"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Arcturus on 2008-02-15
I don't mind the default fonts that are with Ubuntu right now, but I tend to change preferences quite often. Where exactly can I find fonts for Ubuntu and how do I install them?

Still very new. ](*,)

---

### Post by stevejesus on 2008-02-15
This might help;
[http://ubuntu-tutorials.com/2007/10/30/installing-redhats-free-liberation-fonts/]("http://ubuntu-tutorials.com/2007/10/30/installing-redhats-free-liberation-fonts/")

---

### Post by stevejesus on 2008-02-15
There is also a program called Automatix that will install MS fonts and Red Hat liberation fonts for you.  But alot of people might try and steer you away from Automatix.  I think you should be alright...

---

### Post by jordanmthomas on 2008-02-15
> **stevejesus said:**
> There is also a program called Automatix that will install MS fonts and Red Hat liberation fonts for you.  But alot of people might try and steer you away from Automatix.  I think you should be alright...
I'm one of those people, especially when it's easier to install those fonts than it is to install Automatix and then install the fonts.

```
sudo apt-get install msttcorefonts
```
of look for msttcorefonts in Synaptic.


:Also, a good place to find fonts (for design, not so much UI stuff) is [http://www.dafont.com](http://www.dafont.com)
:  I'm a big fan of the artwiz fonts (look in Synaptic)
:  Just look up fonts on the internet and you're bound to find some.



Finally, once you find a font you want to install here's how:
1.  Make sure you have a folder in your home directory called .fonts
```
mkdir ~/.fonts
```
2.  Drop the fonts in this folder (using nautilus or whatever you want).  To make nautilus show hidden folders (.fonts is hidden because of the . at the front) press ctrl - h
3.  Run
```
sudo fc-cache -f
```
and the fonts will be installed.  Have fun.

---

### Post by stevejesus on 2008-02-15
Thats helpful.  I was unaware those were in the regular ubuntu repos.

---

### Post by jordanmthomas on 2008-02-15
Well, you used to have to enable the multiverse repository, but now multiverse and universe are enabled by default.

---

### Post by Arcturus on 2008-02-15
Thanks guys. :KS

---

