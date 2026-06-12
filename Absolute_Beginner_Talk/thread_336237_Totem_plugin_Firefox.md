---
title: "Totem plugin Firefox"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by luvinit on 2007-01-11
I have a situation where firefox 2 occasionally plays embedded video bu usually not. I am guessing it is because i don't appear to have totem firefox plugin installed. Now which one do I need, gstreamer or xine version, I don't understand? Normally I would just have a go, but synaptic says it must uninstall stuff, specifically the ubuntu-desktop, which kinda sounds serious to me.  Am I worried about nothing?

---

### Post by r4ik on 2007-01-11
Try,

sudo apt-get install totem-gstreamer-firefox-plugin

Good luck !

---

### Post by ComplexNumber on 2007-01-11
> **luvinit said:**
> I have a situation where firefox 2 occasionally plays embedded video bu usually not. I am guessing it is because i don't appear to have totem firefox plugin installed. Now which one do I need, gstreamer or xine version, I don't understand? Normally I would just have a go, but synaptic says it must uninstall stuff, specifically the ubuntu-desktop, which kinda sounds serious to me.  Am I worried about nothing?
totem works better with xine that gstreamer. install totem-xine. this will uninstall totem-gstreamer. you will find that totem will have more functionality.

---

### Post by luvinit on 2007-01-11
thanks a lot guys, I'm still interested in what remove ubuntu-desktop means though, if someone can clarify what that is?

---

### Post by ComplexNumber on 2007-01-11
> **luvinit said:**
> thanks a lot guys, I'm still interested in what remove ubuntu-desktop means though, if someone can clarify what that is?
its just a metapackage. when you install a metapackage, it will install a collection of software that goes with that metackage along with the metapackage itself. the actual metapackage is merely a 'container'. you can uninstall it safely.

its a bit like when you buy some sardines that come in a tin(ie the metapackage), together with the sauce. once you've emptied out the sardines and sauce into your plate, there is no more need for the actual tin(ie metapackage). therefore, you can throw it away(ie uninstall it).

---

### Post by luvinit on 2007-01-11
thanks for clearing that up, it made me think it might mess something up.

---

### Post by luvinit on 2007-01-11
problem, get the following message error

totem-xine-firefox-plugin:
  Depends: totem-xine (=1.4.3-0ubuntu1) but 2.16.2-0ubuntu1 is to be installed

---

### Post by luvinit on 2007-01-11
if it is impossible to use totem for embedded video is there an alternative?

---

### Post by luvinit on 2007-01-11
OK, for anyone who is interested further, absolutely no media player plugins beside flash installed from synaptic work for me. Apparently it is not that unusual and it can be fixed by executing the script that this very helpful person wrote:

[http://www.ubuntuforums.org/showthread.php?t=323181&highlight=mplayer+wmv](http://www.ubuntuforums.org/showthread.php?t=323181&highlight=mplayer+wmv)

---

### Post by r4ik on 2007-01-11
I am interested and glad you found a work-around.
Just cant be behind the comp all the time :)

Here is a little read that might help some more,

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Good luck !

---

