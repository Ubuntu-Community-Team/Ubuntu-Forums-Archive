---
title: "Would you tell me exactly how to install a repo?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by ahuman on 2008-02-24
[COLOR="DarkRed"][B]i got these instructions, but they don't make sense to me, would you please tell me exactly step-by-step how to do what those instructions say, except tell me in layman terms, please?

Instructions I was referring to:[/B][/COLOR]
> Add this repo in "system>admin>software sources" or /etc/apt/sources.list
```
deb http://ubuntu.beryl-project.org edgy main
```

**[COLOR="DarkRed"]If I type that code in my terminal, will the repo, automatically be added to my system>admin>software sources" or /etc/apt/sources.list[/COLOR]**

---

### Post by wireddad on 2008-02-24
>System>Software Sources>Third Party Software>copy and paste 
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

---

### Post by tango_ninja on 2008-02-24
you need to add this line of code (repository) to your repository sources list. This is a text file found in your computer directory under  **/usr/apt/sources.list**

to modify this file, use gedit:

```
sudo gedit /etc/apt/sources.list
```

add your line to this text file, save and close. mission accomplished :)    make sense?

---

### Post by ahuman on 2008-02-24
[COLOR="DarkRed"][B]Is Ubuntu 7.10 already equipped with "Edgy Main"? Or would I need to install it to make that repo work for me?

The repo I'm referring to:[/B][/COLOR]
> Add this repo in "system>admin>software sources" or /etc/apt/sources.list
```
deb http://ubuntu.beryl-project.org edgy main
```
**[COLOR="Red"]After I followed those instructions I got an error-message (seen below). What should I do after I get the following error-message? Should I install "edgy main" (or is it built in to Ubuntu 7.10-Gusty)?: [/COLOR]**

[img]http://img229.imageshack.us/img229/4536/screenshotsourceslistusrs5.png[/img]

---

### Post by ahuman on 2008-02-24
**Is Ubuntu 7.10 already equipped with "Edgy Main"? Or would I need to install it to make that repo work for me?**

---

### Post by tango_ninja on 2008-02-24
code should be:
```
sudo gedit /etc/apt/sources.list
```

my mistake :confused:

---

### Post by warbird on 2008-02-24
ahuman: theres no need making a new topic on this, when you're already getting help.

---

### Post by JoshuaRL on 2008-02-24
> **tango_ninja said:**
> code should be:
```
sudo gedit /etc/apt/sources.list
```

my mistake :confused:

Actually, it would be better to use:
```

gksu gedit /etc/apt/sources.list

```
A good rule of thumb to stay away from broken permissions is to use "sudo" for terminal commands, and "gksu" (or graphical sudo) for graphical apps.

---

### Post by JoshuaRL on 2008-02-24
ahuman, do you mind me asking why you want Beryl installed?  It has been merged with Compiz-core so that it is now called Compiz-Fusion.  It is installed by defalult in Gutsy.

So please post what are you looking for and we'll see if we can find an answer.

---

