---
title: "How to install pidgin"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-05-05
i extracted the files but when i click on the install.sh it wont open, whats the terminal command?

---

### Post by Happy_Man on 2007-05-05
```
cd /folder/the/file/is/in
./install.sh
```

---

### Post by bionnaki on 2007-05-05
[http://ubuntuforums.org/showthread.php?t=404508](http://ubuntuforums.org/showthread.php?t=404508)

---

### Post by pay on 2007-05-05
Try```
sudo aptitude install build-essential libglib2.0-dev 
sudo apt-get build-dep gaim
cd pidgin*
./configure
make
sudo make install
```

---

### Post by picpak on 2007-05-05
Or if you want to be really lazy about it you can get it at [getdeb.net](http://www.getdeb.net/app.php?name=Pidgin).

---

### Post by shanike on 2007-05-09
i've tried to compile pidgin on my own but appearently it didn't work out > after installation i was able to run the application by alt+f2... it ran for about 10 seconds. now i can't run pidgin in any way, buddy list pops out for approx. 2secs and then disappears. i tried to reinstall it using various .debs, no luck either :(

---

### Post by misfitpierce on 2007-05-09
Indeed I got it already in deb form I believe from getdeb.net and sounds didnt work and also I prefer gaim atm.

---

### Post by FrancoNero on 2007-05-09
I know this has been asked before, but... when is this gonna be installable through synaptic or add/remove programs?

---

### Post by HydroDiOxide on 2007-05-10
I was wondering how I could uninstall pidgin. I've compiled it and installed it, but I can't find it in Synaptic. Also, can I remove the pidgin (extracted) folder from my desktop?

Kinda new to it all.

---

### Post by uberushaximus on 2007-05-10
> **HydroDiOxide said:**
> I was wondering how I could uninstall pidgin. I've compiled it and installed it, but I can't find it in Synaptic. Also, can I remove the pidgin (extracted) folder from my desktop?

Kinda new to it all.

Unfortunately if you used "sudo make install" you have to manually remove all of the files that the makefile creates.

---

### Post by zvacet on 2007-05-10
> deb [http://acorbeaux.free.fr/ubuntu](http://acorbeaux.free.fr/ubuntu) feisty main

Put this in your source list and you will get Pidgin

---

### Post by jputman01 on 2007-05-10
> **uberushaximus said:**
> Unfortunately if you used "sudo make install" you have to manually remove all of the files that the makefile creates.

sudo make uninstall???

---

### Post by HydroDiOxide on 2007-05-11
> **jputman01 said:**
> sudo make uninstall???

Right, and that is 'uninstall' from the same folder I gave the install command (that is the extracted folder on my Desktop)?

---

### Post by Zeikcied on 2007-05-11
> **misfitpierce said:**
> Indeed I got it already in deb form I believe from getdeb.net and sounds didnt work and also I prefer gaim atm.

So I'm not the only one who doesn't have any sound from the Pidgin deb installer from that site?

I'm using Kubuntu, and I have the GStreamer files, and Pidgin doesn't play any sounds.  Though, I guess it's better than nothing.

---

### Post by metroplex on 2007-05-30
> **uberushaximus said:**
> Unfortunately if you used "sudo make install" you have to manually remove all of the files that the makefile creates.

Or you could (from the pidgin sources-directory) run "sudo make uninstall" to have the Makefile do the job of uninstalling Pidgin.

---

### Post by screaminj3sus on 2007-05-30
> **zvacet said:**
> Put this in your source list and you will get Pidgin

Thank you so much, the repo is a bit slow, but the upgrade to pidign went perfectly.

---

### Post by ryry0666 on 2007-08-11
> **uberushaximus said:**
> Unfortunately if you used "sudo make install" you have to manually remove all of the files that the makefile creates.

You can use make uninstall as root. but you might have to run ./configure first.

```

cd /path/to/pidgin/source
./configure
sudo make uninstall

```

---

### Post by Ozztopia on 2007-11-28
'sudo make uninstall' works well to uninstall pidgin if it was compiles from source. The command has to given, as mentioned in earlier posts, in the directory of the source from where it was compiled earlier.

---

### Post by Tony3286 on 2007-11-29
Why don't you give KOPETE a try? Its a KDE instant messaging  program but works great with Gutsy AND supports Video which is why I switched.

[http://kopete.kde.org/](http://kopete.kde.org/)

---

### Post by niceguy123 on 2007-12-28
> **Tony3286 said:**
> Why don't you give KOPETE a try? Its a KDE instant messaging  program but works great with Gutsy AND supports Video which is why I switched.

[http://kopete.kde.org/](http://kopete.kde.org/)

I looked at Kopete website and don't see that it supports googlechat is that right?

Is there a platform that also supports sending SMS text messages to mobile phones via icq?

---

### Post by markyb86 on 2007-12-28
> **niceguy123 said:**
> 

Is there a platform that also supports sending SMS text messages to mobile phones via icq?

just use AIM and add the cell phone number as a buddy like "+13304677474"  (no quotes)

---

### Post by niceguy123 on 2008-01-07
> **markyb86 said:**
> just use AIM and add the cell phone number as a buddy like "+13304677474"  (no quotes)

OK, but can I do the same with Pidgin?

---

### Post by FenderGuy2112 on 2008-01-07
Isn't Pidgin already installed with Ubuntu?

FenderGuy2112

---

