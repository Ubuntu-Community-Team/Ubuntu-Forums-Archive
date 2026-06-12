---
title: "[SOLVED] Gnome vrs kde"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-09-06
I have been using Gnome sine I first installed Ubuntu, but am interested in trying kde. What are the advantages/dis-advantages of kde over Gnome? Also how can I install/remove it if I decide to give itr a try. Any opinions will be appreciated.  Ubuntu rocks:guitar:

---

### Post by WebSiteGuru on 2007-09-06
Nothing different just preference I think!
```
sudo aptitude install kubuntu-desktop
```

---

### Post by silent1643 on 2007-09-06
you can try kde for yourself,

Code:
sudo apt-get install kde-core

[http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)

and uninstall it if you do not like 

Code:
sudo apt-get remove kde-core

---

### Post by dptxp on 2007-09-06
The kde-core is a smaller package and you can even retain it, choose Gnome or KDE at time of log in.
60 MB download I guess.

You can do a lot more with kde, but Gnome is much easier to navigate. Gnome is more robust too.

sudo aptitude update
sudo aptitude install kde-core

To remove
sudo aptitude remove kde-core.

You will get some kde programs added to Gnome Menu

---

### Post by skyjacker on 2007-09-06
Thanks for the info. I may try it, but sounds like Gnome is easier.

---

### Post by deadgobby on 2007-09-06
I think this link will give you more information. It is up to you what you feel confy with.
[http://psychocats.net/ubuntu/kdegnome](http://psychocats.net/ubuntu/kdegnome)
  Both are great, but it is up you which one you want to use.

Gobby

---

### Post by dca on 2007-09-06
They both take time to learn all the nuance and navigation.  Both are excellent desktop environments but as had been stated it all boils down to preference...

---

### Post by skyjacker on 2007-09-06
> **deadgobby said:**
> I think this link will give you more information. It is up to you what you feel confy with.
[http://psychocats.net/ubuntu/kdegnome](http://psychocats.net/ubuntu/kdegnome)
  Both are great, but it is up you which one you want to use.

GobbyThanks for this info.  Just what I needed to know. I'll read it over before I decide.

---

### Post by deadgobby on 2007-09-06
I am glad to help and will help out any time. It is up to you. Enjoy the freedom of Linux.
Gobby

---

### Post by alex_anthony on 2007-09-06
using aptitude instead of apt-get would be advisable, as it makes it easier if you want to uninstall later

---

### Post by WebSiteGuru on 2007-09-06
> **alex_anthony said:**
> using aptitude instead of apt-get would be advisable, as it makes it easier if you want to uninstall later

To my understanding yes, after I read some where in the forums that using aptitude to install/remove will also install/remove all the dependencies needed that was installed with the apps.

---

### Post by igknighted on 2007-09-06
> **WebSiteGuru said:**
> To my understanding yes, after I read some where in the forums that using aptitude to install/remove will also install/remove all the dependencies needed that was installed with the apps.

apt-get has done this since edgy, that difference is from back in the dapper days.  Now "apt-get autoremove" does the exact same thing.

---

