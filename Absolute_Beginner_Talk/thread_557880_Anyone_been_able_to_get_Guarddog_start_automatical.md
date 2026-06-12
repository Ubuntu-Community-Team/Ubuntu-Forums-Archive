---
title: "Anyone been able to get Guarddog start automatically with Gnome desktop?"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-09-23
I prefer Guarrdog to Firestarter, however with both gnome and kubuntu desktops installed I have need been able to get Guarddog to setup up the iptables at boot when using Gnome.  Im not sure is adding it to the sessions menu would help, b/c when Firestarter is added, if the network isnt up when firestarter runs, the program exits.  

Any suggestions.???

---

### Post by kellemes on 2007-09-23
[http://ubuntuforums.org/showthread.php?t=449319]("http://ubuntuforums.org/showthread.php?t=449319")
[http://ubuntuguide.org/wiki/Ubuntu:Feisty/Security#How_to_make_the_Firestarter_GUI_start_automatically_at_startup]("http://ubuntuguide.org/wiki/Ubuntu:Feisty/Security#How_to_make_the_Firestarter_GUI_start_automatically_at_startup")

---

### Post by stimpack on 2007-09-23
Can't help you with Guarddog sorry, but wanted to say that Firestarter (which I use under KDE) is just a GUI for altering iptables, it doesnt matter if it starts or not, your iptables are set the same from last time you used it. You only launch Firestarter when you want to change something, then you can quit it. Guarddog maybe the same, but I have not tried it yet.

---

### Post by kevdog on 2007-09-23
Im not sure if some of the info Im getting from you guys is totally accurate.  If firestarter is started during the login process before the network is up, the iptables are not set.  I dont think the iptables are preserved between log offs, but rather need to be set everytime the computer starts.  Thats the exact problem I am having with Guarddog.  I set the IPtables, however after reboot, I have to restart the program manually, to reset the IPtables.  There are a lot of posts in the forums with people complaining how Firestarter doesnt start at startup for various reasons.

---

### Post by stimpack on 2007-09-24
Because people think they need to have it running all the time. I am afraid I am only talking with certainty about Firestarter here, not Guarddog. The only time Firestarter ever changes your iptables is when you click the 'apply rules' button, then its set forever.

Network is up before login.

---

