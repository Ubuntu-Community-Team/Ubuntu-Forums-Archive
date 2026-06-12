---
title: "installing sharutils package w/o internet"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by andrewsco on 2006-01-17
I am trying to set up my wireless card wg311t and have been advised to try do it through madwifi. In order to follow a tutorial:

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

I need to install sharutils. Now I have no internet connection - is there a way to install it some other way? Does anyone have a link to a file I can save on my flash drive? 

Once I have it - where would you suggest saving it? and how do I install it (with what command or program?)

Sorry for all the questions and little knowledge -I'm just fed up of not being able to get the internet. If linux is such a good platform you would think you could quite easily get the internet wouldn't you.

Andrew

---

### Post by Kapre on 2006-01-17
[QUOTE=andrewsco]I am trying to set up my wireless card wg311t and have been advised to try do it through madwifi. In order to follow a tutorial:

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo) [/quote]

Andrew - please check this [thread (thanks to Lambert)]("http://ubuntuforums.org/showthread.php?t=105437") for your madwifi.

Hope this help.

K

---

### Post by Lambert on 2006-01-17
I'm not sure sharutils is needed. My tutorial you do need internet access but I can tell you here what to do if you don't have access.

You can download madwifi-ng-current.tar.gz from here.

[http://snapshots.madwifi.org/](http://snapshots.madwifi.org/)

Then copy this file to /usr/src

```
sudo cp /path/to/file.madwifi-ng-current.tar.gz /usr/src/
```

then untar the file

```
sudo tar zxvf madwifi-ng-current.tar.gz
```

Everything else you need such as gcc-3.4 kernel headers etc.. should all be on the install cd if you need it.

From here just follow the rest of the howto.

---

### Post by Lambert on 2006-01-17
I'm not sure sharutils is needed. My tutorial you do need internet access but I can tell you here what to do if you don't have access.

You can download madwifi-ng-current.tar.gz from here.

[http://snapshots.madwifi.org/](http://snapshots.madwifi.org/)

Then copy this file to /usr/src

```
sudo cp /path/to/file.madwifi-ng-current.tar.gz /usr/src/
```

then untar the file

```
sudo tar zxvf madwifi-ng-current.tar.gz
```

Everything else you need such as gcc-3.4 kernel headers etc.. should all be on the install cd if you need it.

From here just follow the rest of the howto.

---

