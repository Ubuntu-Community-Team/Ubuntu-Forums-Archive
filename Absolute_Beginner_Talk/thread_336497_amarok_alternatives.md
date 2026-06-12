---
title: "amarok alternatives?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by manutdfan2850 on 2007-01-11
Hi, I am looking or an Amarok alternative. I really like Amarok, especailly how it gets Lyrics and album artwork, But I dont like how its only for KDE and I am running Ubuntu Dapper. I do not want to install KDE just to be able to support themes on it. 

for these reasons I am asking if anyone knows of other media players with similar functions as Amarok like the lyrics fetching, and album artwork, etc. but for Gnome

plz let me know.

Thanks in advance

---

### Post by jvc26 on 2007-01-11
Not true: Amarok in Ubuntu:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28amaroK.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28amaroK.29)
You can use basically all KDE apps in Gnome and Gnome apps in KDE. :) enjoy!
Il

---

### Post by manutdfan2850 on 2007-01-11
i know, I have Amarok in ubuntu but I dont like how my gtk themes wont apply to this one app. and it just looks crappy. not saying its a bad program, in fact, i love amaroK but if it was gnome based i would really love it more.  for the reason i mentioned.

right now this is the only app i use that is kde based so im looking for a gnome alternative. plus i dont want to install kde on my ubuntu because it will bloat my system. 

im testing out Exaile, found it by searching on google,   will let you know if it suits my needs

link if anyone else is interested: [http://www.exaile.org/trac](http://www.exaile.org/trac)

---

### Post by jvc26 on 2007-01-11
Ah right ok - misunderstood you in your initial post thought you meant it wouldnt work :)
Il

---

### Post by patagonik on 2007-01-11
**Listen** is a good alternative i guess... [http://listengnome.free.fr/index.php?nom_page=home](http://listengnome.free.fr/index.php?nom_page=home)

Give a try! 

pata

---

### Post by habtish on 2007-01-11
> **manutdfan2850 said:**
> Hi, I am looking or an Amarok alternative. I really like Amarok, especailly how it gets Lyrics and album artwork, But I dont like how its only for KDE and I am running Ubuntu Dapper. I do not want to install KDE just to be able to support themes on it. 

for these reasons I am asking if anyone knows of other media players with similar functions as Amarok like the lyrics fetching, and album artwork, etc. but for Gnome

plz let me know.

Thanks in advance

Exaile [[http://www.exaile.org/trac]](http://www.exaile.org/trac]) is the Gnome equivallent of amarok. It covers most of Amaroks' finctionalities and comes with a few extras (availavle plugins)
you can get it from the repos I believe.
```
sudo apt-get update
sudo apt-get install exaile
```

You can read the review on linux.com posted recently before installing [here]("http://applications.linux.com/article.pl?sid=07/01/03/2140240&tid=39&tid=13")
Hope this was what you were looking for...

---

### Post by manutdfan2850 on 2007-01-11
> **habtish said:**
> Exaile [[http://www.exaile.org/trac]](http://www.exaile.org/trac]) is the Gnome equivallent of amarok. It covers most of Amaroks' finctionalities and comes with a few extras (availavle plugins)
you can get it from the repos I believe.
```
sudo apt-get update
sudo apt-get install exaile
```

You can read the review on linux.com posted recently before installing [here]("http://applications.linux.com/article.pl?sid=07/01/03/2140240&tid=39&tid=13")
Hope this was what you were looking for...

getting this error by the method you posted:
> sudo apt-get install exaile
Reading package lists... Done
Building dependency tree... Done
Package exaile is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package exaile has no installation candidate



---

### Post by Tasu on 2007-01-11
> **manutdfan2850 said:**
> getting this error by the method you posted:

Indeed! You have to download it from the website ([http://www.exaile.org/trac/wiki/Releases)](http://www.exaile.org/trac/wiki/Releases)), it's still not in the repositories, however is a really good alternative to amarok, I use it day by day and is my preferred over Listen, Banshee or Rythmbox.
On the web site you can find debs easily installable via gdebi.

enjoy ^_^

---

### Post by Albi on 2007-01-11
Might wanna give this a shot
[http://www.songbirdnest.com/](http://www.songbirdnest.com/)

Very similar to itunes, but in early beta though

---

### Post by manutdfan2850 on 2007-01-11
ok i installed it using the deb on the website. : 0.2.8 Ubuntu (Dapper) i386 Package (Thanks Chris Borga)

but when i click on the Exaile icon in Sound/Video nothing happens. nothing opens up at all. 

what could be the problem.

system restart did not fix it.

---

### Post by habtish on 2007-01-11
sorry about that, I do use the app but had forgotten how I had installed it. You can download the Dapper .deb [here]("http://www.exaile.org/files/exaile_0.2.8_i386dapper.deb") and install from there. Enjoy~

---

### Post by pormogo on 2007-01-11
wow that songbird application looks awesome, when I get my internet back up and running at my new place tomorrow I think I might give that a shot :)

---

### Post by Albi on 2007-01-11
run exaile in terminal (open it up and type "exaile') and what happens?

Edit: Try the .deb package before doing this

---

### Post by manutdfan2850 on 2007-01-11
this is what i get: 
> laptop:~$ exaile
Traceback (most recent call last):
  File "/usr/bin/exaile", line 61, in ?
    from xl import *
  File "/usr/share/exaile/xl/tracks.py", line 18, in ?
    import common, media, db, config, trackslist
  File "/usr/share/exaile/xl/media.py", line 19, in ?
    import mutagen, mutagen.id3, mutagen.flac, mutagen.oggvorbis
ImportError: No module named oggvorbis

i have no idea what this means

---

### Post by habtish on 2007-01-11
do you have the required packages?

[LIST]
[*]Python 2.4
[*]python-gtk2 (2.8.6)
[*]gstreamer 0.10, gstreamer0.10-plugins-good
[*]python-dbus
[*]python-pysqlite2
[*]python-mutagen[/LIST]

---

### Post by Albi on 2007-01-11
Ok, from here [http://www.ubuntuforums.org/showthread.php?t=293307](http://www.ubuntuforums.org/showthread.php?t=293307)

It says to do this:
```
wget http://www.sacredchao.net/~piman/software/mutagen-1.8.tar.gz
tar xvfz mutagen-1.8.tar.gz
cd mutagen*
./setup.py build
sudo ./setup.py install
```

---

### Post by manutdfan2850 on 2007-01-11
> **habtish said:**
> do you have the required packages?

[LIST]
[*]Python 2.4
[*]python-gtk2 (2.8.6)
[*]gstreamer 0.10, gstreamer0.10-plugins-good
[*]python-dbus
[*]python-pysqlite2
[*]python-mutagen[/LIST]

yup got em.

> **Albi said:**
> Ok, from here [http://www.ubuntuforums.org/showthread.php?t=293307](http://www.ubuntuforums.org/showthread.php?t=293307)

It says to do this:
```
wget http://www.sacredchao.net/~piman/software/mutagen-1.8.tar.gz
tar xvfz mutagen-1.8.tar.gz
cd mutagen*
./setup.py build
sudo ./setup.py install
```

trying now will post if it works or not

thanks for such quick replies :D

edit: it works!!! thanks for your help! 

thanks again!

---

### Post by matt_risi on 2007-01-11
Yikes, unstable and no iPod support here.

---

### Post by r4ik on 2007-01-11
> **matt_risi said:**
> Yikes, unstable and no iPod support here.

Tools Preferences.
if it works dont no havent got an iPod

---

### Post by thewump on 2007-01-11
Rhythmbox is awesome.

In plugins you can select artwork and lyrics and get both.  It's also VERY itunes like ( which I personally like ).

Keith

---

### Post by imon9 on 2007-01-14
i need help with exaile, if anyone could be of any help, i would really be glad...

i install exaile, with all dependencies fulfill, but it does not run after i click the icon. type exaile in terminal gave me this error:

  File "/usr/bin/exaile", line 26, in <module>
    import xl.dbusinterface
  File "/usr/share/exaile/xl/dbusinterface.py", line 18, in <module>
    import dbus
ImportError: No module named dbus

anyhow, i am sure dbus is install, so is the rest of the stuff, only thing i am not sure is that i read that dbus and python must some how be same version or someting. I can remove the install version of python-dbus now since the synaptic installer will want to remove add/remove program, update manager and exaile with it all togther, which sound like really crazy

i downloaded many deb, but they all wont let me install saying it conflict with the one i have in my system...

any simple solution for me please?

btw, i as well like amarok, but damn KDE is what i dont dig...

thanks in advance

---

