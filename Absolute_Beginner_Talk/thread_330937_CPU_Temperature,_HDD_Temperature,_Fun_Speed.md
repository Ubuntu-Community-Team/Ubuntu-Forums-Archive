---
title: "CPU Temperature, HDD Temperature, Fun Speed"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by sinnerman on 2007-01-03
Does anybody install packages for monitoring cpu, hdd temperature and fun speed.

If y. please write installation steps and which packages use.

Thx.

---

### Post by taurus on 2007-01-03
[http://www.lm-sensors.org/](http://www.lm-sensors.org/)

---

### Post by sinnerman on 2007-01-03
Thx.

---

### Post by sinnerman on 2007-01-04
I try install hardware sensores with Synapitic Package Manager and when I finish instalation and put applet on panle I get message "[COLOR="Red"]No sensors found[/COLOR]". Does anybody have the same problem. 

Thx

---

### Post by Pathfinder_ on 2007-01-04
[http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors+install]("http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors+install")
that how-to worked for me in dapper. i dunno if it works in edgy since i haven't tried it but I'm guessing that it should.
EDIT: I just tried it and it worked, but i skipped the last part where you have to load the sensors because i had a problem with it in dapper, so i just restarted my comp and it works.

---

### Post by sinnerman on 2007-01-04
Thx. It`s greate thread!

sinnermans Drapper with enabled sensors :-)

[IMG]http://i147.photobucket.com/albums/r314/sinnerman8/Screenshot.png[/IMG]

---

### Post by motin on 2008-02-20
```
sudo apt-get install computertemp
```

This will install a GNOME Applet that monitors your CPU temp

---

### Post by justleen on 2008-02-20
have a look at[ conky,]("http://conky.sourceforge.net/") if you like numbers and stats :)

---

### Post by Vivian-Synecdoche on 2008-05-22
> **motin said:**
> ```
sudo apt-get install computertemp
```

This will install a GNOME Applet that monitors your CPU temp

Hi - do you know if there's something similar to computertemp for hard drive temp?

thanks.

*UPDATE*: whoops - I just found out how to do it. Computertemp panel applet! has an option in preference to monitor (surprise, surprise...) hddtemp! awesome app. thanks. So now I've two applets: one checking my rather hot CPU temp and my relatively cooler HDD temp. coolios.

---

### Post by seamustry on 2008-05-22
i installed computertemp but how do i run it? i can't find it anywhere...

---

### Post by iwannalearn on 2008-05-22
> **seamustry said:**
> i installed computertemp but how do i run it? i can't find it anywhere...


I just tried it went to Synaptic Package Manager did serch for hddtemp and installed hddtemp & sensors applet aswell as the above computertemp

then right click in the top bar and add to panel and from there i select them.

---

