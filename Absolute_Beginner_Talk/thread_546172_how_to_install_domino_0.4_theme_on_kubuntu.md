---
title: "how to install domino 0.4 theme on kubuntu?"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by kazuya on 2007-09-08
how do I install domino 0.4 on My Kubuntu install? It says something about compiling.

Is there a domino theme for kubuntu? I am really trying to get Kubuntu to look like archlinux's kdemod which uses domino style.

[http://www.kde-look.org/content/show.php/Domino?content=42804](http://www.kde-look.org/content/show.php/Domino?content=42804)

---

### Post by kellemes on 2007-09-08
Download the tarbal and to install you can point-click the theme from KDE's controlcenter.

---

### Post by sumguy231 on 2007-09-08
Since it is not packaged for Ubuntu, you will need to compile it yourself. To do this:
-Extract the .tar.gz to a folder
-Do this:
```

./configure
make
sudo make install

```

> Download the tarbal and to install you can point-click the theme from KDE's controlcenter.
That only works for theme manager themes as far as I know. And Domino is not one.

---

### Post by kazuya on 2007-09-11
the .config instruction did not work for me. <Anymore ideas.

---

### Post by Maestro23 on 2007-09-11
> **kazuya said:**
> the .config instruction did not work for me. <Anymore ideas.

At what point did you run into trouble?  Do you have "build-essential" installed for compiling from source?

Check the "How to compile program from source" Section: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_compile_a_program_from_source_code](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_compile_a_program_from_source_code)

---

### Post by kazuya on 2007-09-12
after ./configure

checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!
kazuya@kazuya-desktop:~/Desktop/42804-domino-0.4/domino-0.4$ make
make: *** No targets specified and no makefile found.  Stop.

---

### Post by jordanmthomas on 2007-09-13
1.   kdemod is pure deliciousness, as is archlinux as a whole.
2.   You need to install the X headers (and maybe build-essential if you don't have it, along with some kdelibs)
```
sudo apt-get install build-essential xorg-dev qt3-apps-dev kdebase-dev kdelibs-dev automake
```
Then run your ./configure again
You may need more libraries after this, even.  The errors from ./configure should at least give you some clue as where to head.

**edit** and to tease you and make you want to keep going until you get it installed, a screenshot :p

---

### Post by kazuya on 2007-09-18
Did not work for me. It failed at even sudo apt-get install build-essential xorg-dev qt3-apps-dev kdebase-dev kdelibs-dev automake  
step.

Is there a working domino theme for kubuntu?

---

### Post by kellemes on 2007-09-18
Am I missing something here?
There is a working .deb you can point-click install with gdebi (among others).
[http://www.kde-look.org/content/show.php?content=52864&forumpage=0]("http://www.kde-look.org/content/show.php?content=52864&forumpage=0")

---

### Post by kazuya on 2007-09-18
thanks for pointing that one out. I shall try it. I saw other ones and those failed for me; But not this one.. I shall try it out. The 32 bit version.

---

