---
title: "Do not have add/remove"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by motox16 on 2006-10-14
I'm sorry if this has already been posted but as you can guess I am new to linux and I want to install things but I cannot find that add/remove thing under applications at the top that you guys use. Any help would be most appreaciated.

---

### Post by meng on 2006-10-14
I don't know why you can't find it, but even if it was there I wouldn't recommend using it. Use System > Admin > Synaptic Package Manager instead. Add/Remove often doesn't work very well.

---

### Post by jorn on 2006-10-14
If I do understand you correct, you want to install applications?
Go to: System>Administration>Synaptic Package Manager
Rightclick apps. choose install and click the button Aply on the top.
You can also install through the terminal.

---

### Post by opticsnake on 2006-10-14
There's a great guide on adding apps using the command line at

[http://ubuntuguide.org/wiki/Dapper]("http://ubuntuguide.org/wiki/Dapper")

---

### Post by aysiu on 2006-10-14
If you right-click on the Applications menu, you can **Edit Menus** and make sure the Add/Remove Programs box is checked (or ticked, if you're not American).

If there is no Add/Remove Programs, add a new menu entry and use the command ```
gksudo gnome-app-install
``` If you don't have *gnome-app-install* installed, you can install that through Synaptic Package Manager

Great tutorial on Synaptic here:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by motox16 on 2006-10-15
okay, I'm on windows right now I will boot to linux in a sec to try this thanks for the help.

---

### Post by motox16 on 2006-10-15
ok, I downloaded the flash plugin for mozilla firefox. I went to Synaptic and searched for it but found nothing. I tried following that tutorial but from what I understand you can only install stuff that is on the ubuntu server this program is reading off. Is there any way that I can get flash on here? I have downloaded the linux version so I know there must be a way.

---

### Post by ThrobbingBrain66 on 2006-10-15
you have to enable some extra repositories.  this list should be a good start.

[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

In a terminal, type
```
sudo gedit /etc/apt/sources.list
```

replace the text in this file with the text from the link.

then type
```
sudo aptitude update
```

from there you can go to synaptic and search for flashplugin-nonfree

---

### Post by aysiu on 2006-10-15
> **motox16 said:**
> ok, I downloaded the flash plugin for mozilla firefox. I went to Synaptic and searched for it but found nothing. I tried following that tutorial but from what I understand you can only install stuff that is on the ubuntu server this program is reading off. Is there any way that I can get flash on here? I have downloaded the linux version so I know there must be a way.
This will help you get Flash installed--comes with screenshots to help you out, too:
[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)

---

