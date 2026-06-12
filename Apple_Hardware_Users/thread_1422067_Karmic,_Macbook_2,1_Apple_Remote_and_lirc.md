---
title: "Karmic, Macbook 2,1 Apple Remote and lirc"
date: 2010-03-05
forum: Apple Hardware Users
---

### Post by Pseudo-Morph on 2010-03-05
Hello All,

I'm having a problem getting the apple remote on my Macbook 2,1 to work with Karmic and am looking for a little advice. 

I have followed the guide here [https://help.ubuntu.com/community/MacBook2-1/Karmic](https://help.ubuntu.com/community/MacBook2-1/Karmic) and utilised the extended .lircrc in the first post of this thread [http://ubuntuforums.org/showthread.php?t=502924](http://ubuntuforums.org/showthread.php?t=502924) linked to by the guide however I cannot get any action from my remote (it does work in OSX).

The problem, I believe, lies in where Gnome needs to start irexec and irxevent. 

Running irexrc -d from a terminal gives no output but I can also not find a process running after launch.

Running irxevent -d returns 'irxevent: could not connect to socket irxevent: No such file or directory'

I have also installed gnome-lirc-properties which (until a recent reboot) reported that there was no IR daemon running.

So now I'm stuck as to where to look next.. any suggestions?

---

### Post by linuxopjemac on 2010-03-05
irxevent is not running as a daemon....maybe a stupid question to start with, but did you install lirc and lirc-x ?
```
sudo apt-get install lirc lirc-x
```

---

### Post by Pseudo-Morph on 2010-03-06
> **linuxopjemac said:**
>  maybe a stupid question to start with, but did you install lirc and lirc-x ?


Not a stupid question, have to start somewhere. Both packages are installed, I've even purged and reinstalled just to be sure as part of my trouble shooting.

---

### Post by linuxopjemac on 2010-03-06
Reading makes you help understand, here is the place:
[http://www.lirc.org/](http://www.lirc.org/)

btw, I can't help...maybe you find a solution there

---

