---
title: "Help with Installing Java"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Nifty Nate on 2008-03-23
Hey, I am new to using Ubuntu and Linux, but I could really use some help.

I just got the Beta of Hardy Heron installed and I am trying to get some things such as Java. Unfortunately, I have no idea how to. Could someone please lead me through the process.

---

### Post by disturbedite on 2008-03-23
open your package manager (synaptic or adept).
find icedtea  (icedtea is a free open source implementation of sun's java)
mark it for installation and click the check mark.
(specifically install: icedtea-java7-bin, icedtea-java7-jre, icedtea-java7-plugin).

---

### Post by kalesh7 on 2008-03-23
some things may not work with icedtea (I couldn't get eclipse to work) in such case install sun-java6-jre using sypnatic or similar

---

### Post by smartboyathome on 2008-03-23
1) This should be posted in the hardy herron forum, and
2) this is a known bug, java doesn't want to work in Firefox for some reason.
3) I would advise against running a beta if you are a new user. Try running Gutsy instead. :)

---

### Post by disturbedite on 2008-03-24
icedtea works fine for me with fx3 in hardy.  as a matter of fact, it works with everything.  i've not experienced any problems whatsoever with it.

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b5pre) Gecko/2008032404 Minefield/3.0b5pre - Build ID: 2008032404

---

### Post by stchman on 2008-03-24
> **Nifty Nate said:**
> Hey, I am new to using Ubuntu and Linux, but I could really use some help.

I just got the Beta of Hardy Heron installed and I am trying to get some things such as Java. Unfortunately, I have no idea how to. Could someone please lead me through the process.

I know some forum members are going to yell at me, but I have had no problem with the 1.5 version of Java on several machines.  To install Java do the following:

```

sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin
```

If you must use 1.6 then substitute 6 for 5 in the previous statement.

---

### Post by cj2003 on 2008-03-24
There are also a couple of guides:
[Java on Ubuntu in 50 easy steps]("http://ubuntu-news.net/modules/news/article.php?storyid=3037")

or [Flash and Java on 64bit Ubuntu and Kubuntu]("http://ubuntu-news.net/modules/news/article.php?storyid=3952")

---

### Post by djbsteart1 on 2008-03-24
As had been said i would strongly recommend using the stable release which is 7.10, as 8.04 is still being tested and as has been shown here, still has issues. But if you want to stick with the Heron, both Icedtea and Sun's java are available in the repository, however you will need to select all of them in synaptic package manager, not add/remove, or adept in kubuntu. This will give you access to non free, and other software that has been ommited out for various reasons.

---

