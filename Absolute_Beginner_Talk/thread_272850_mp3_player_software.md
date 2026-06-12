---
title: "mp3 player software"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by jasonsexton on 2006-10-07
is there anything better than Amorok out there
I don't like how it organizes songs for me (compilations are split into seperate albums)

or does anyone know if there is a place in Amorok to turn off this feature?

thanks

---

### Post by Perfect Storm on 2006-10-07
Something like Amorok style or something like winamp style?

---

### Post by jasonsexton on 2006-10-07
more like Amorok
as close to iTunes as possible

---

### Post by Perfect Storm on 2006-10-07
Try with Listen and see if it's something for you: [http://ubuntuforums.org/showthread.php?t=126080&highlight=listen](http://ubuntuforums.org/showthread.php?t=126080&highlight=listen)

---

### Post by jasonsexton on 2006-10-07
cool, thank you
anything I need to know about installing the program?  I'm new to Linux/Ubuntu

---

### Post by Perfect Storm on 2006-10-07
Well, you need to add the stable source of Listen in your sourcelist: [http://listengnome.free.fr/index.php?nom_page=download](http://listengnome.free.fr/index.php?nom_page=download)

```
sudo nano /etc/apt/sources.list
```

add:

[b]
## Listen Stable
deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen
deb-src [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen
[/b]

Save and exit <ctrl> + <o> | <ctrl> + <x>

```
sudo apt-get update
```

You can now find it in synaptic (use of the search button in synaptic).

---

### Post by jasonsexton on 2006-10-07
thanks

---

### Post by TheWizzard on 2006-10-07
> **jasonsexton said:**
> is there anything better than Amorok out there
I don't like how it organizes songs for me (compilations are split into seperate albums)

no, amarok is the best. by far!
:D 


> or does anyone know if there is a place in Amorok to turn off this feature?


you can change the grouping in compilation albums with the option "show under various artists".

---

### Post by Marsolin on 2006-10-07
While [Listen]("http://linuxappfinder.com/package/listen") never made it in Dapper, it is in the Edgy repository.

---

### Post by tchoklat on 2006-10-16
I have tried to load LISTEN onto my new dapperinstallation. In Synaptic package manager I get a message telling me that these pacakges have unresolvable dependencies;

listen:
 Depends: python2.4-pymad  but it is not installable
 Depends: python2.4-pysqlite2  but it is not installable
 Depends: python2.4-ctypes  but it is not installable
 Depends: gstreamer0.10-plugins-ugly  but it is not installable

What do I do now. I need an MP3 player.


Tchoklat:-D

---

### Post by Perfect Storm on 2006-10-16
Please post the output of this:
```
cat /etc/apt/sources.list
```

---

### Post by Marsolin on 2006-10-16
Do you have the dapper universe and multiverse repositories enabled? Those dependiencies you are having problems with are in there.

---

