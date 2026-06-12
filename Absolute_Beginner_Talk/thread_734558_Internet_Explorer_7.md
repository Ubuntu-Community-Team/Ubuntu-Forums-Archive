---
title: "Internet Explorer 7"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by hikujk123 on 2008-03-24
I am trying to run IE 7 (I will run older versions if necessary) under wine.  I personally hate IE but want to run Microsoft Access 2000, which requires IE 3.00 or higher.  I would prefer OOo, but it is buggy on my computer (Please don't question me on this :).  No one seemed to know what was wrong on an earlier post, nor was anyone willing to help me install it directly from the website).  All help would be appreciated.  I am running Xubunu 7.10 for AMD64 processors.

---

### Post by scragar on 2008-03-24
[http://www.tatanka.com.br/](http://www.tatanka.com.br/) <-- download and run, check advanced options for the IE7 beta, engine only, still using IE6 skin.

---

### Post by hikujk123 on 2008-03-24
There are only instructions for Fiesty.  I am very new to linux, so won't be able to change the commands without some help.  Is IEs4Linux genuine enough for Access to work?

---

### Post by jpdamigaman on 2008-03-24
I down loaded and installed ie 6 from here

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by smartboyathome on 2008-03-24
ies4linux should do the trick for you. I would suggest running access through Virtualbox if you have an install cd for xp.

---

### Post by scragar on 2008-03-24
replace **version** in commands below with your version, so: **dapper**(6.06), 
**edgy**(6.10), **feisty**(7.04) or **gutsy**(7.10)
```
 sudo gedit /etc/apt/sources.list
```
uncomment/add:
```
deb http://us.archive.ubuntu.com/ubuntu **version** universe
deb http://wine.budgetdedicated.com/apt **version** main
```
Close gedit.
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
 sudo apt-get update
 sudo apt-get install wine cabextract
```
```
 wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
 tar zxvf ies4linux-latest.tar.gz
 cd ies4linux-*
 ./ies4linux
```

as for if you'll be able to run access with it I don't know, I don't know why you can't use open office database though, it run's nativly and tends to run a lot smoother for me(then access used to on windows).

---

### Post by hikujk123 on 2008-03-24
Thanks.  I am going try that.  How do I uninstall it if need be?  Also, for my OOo woes see here: [http://ubuntuforums.org/showthread.php?t=731925](http://ubuntuforums.org/showthread.php?t=731925) and  [http://ubuntuforums.org/showthread.php?t=731790](http://ubuntuforums.org/showthread.php?t=731790)

---

### Post by hikujk123 on 2008-03-24
I get the following output after running the first command:
```
sudo: gedit: command not found
```

Is this because I am running xubuntu?

---

### Post by scragar on 2008-03-24
may be, gedit is the ubuntu default text editor, not sure about the xubuntu one...

---

### Post by smartboyathome on 2008-03-24
Replace gedit with mousepad (I think that is Xubuntu's text editor?), or install gedit.

---

