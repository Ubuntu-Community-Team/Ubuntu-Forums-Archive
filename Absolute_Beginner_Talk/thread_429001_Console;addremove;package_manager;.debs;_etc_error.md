---
title: "Console;add/remove;package manager;.debs; etc error (repost)"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by silentjudas on 2007-04-30
Alright, I have an annoying error that spawned on me the other day. I can't install like, anything anymore (console, package manager, freakin add remove, .debs, etc) because it keeps saying

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

and everytime i run it, it freakin says i have to be a superuser....and i'm the only blinkin' user!


please help.... 

*also: using feisty, in case that helps you any*

*reposted here, made more sense i guess*

---

### Post by Seisen on 2007-04-30
You need to add "sudo" to become a super user

```
sudo dpkg --configure -a
```

---

### Post by oilchangeguy on 2007-04-30
open a terminal and type sudo dpkg --configure -a 
and press enter.

---

### Post by wormser on 2007-04-30
Use **sudo** before a command to become a super user.

sudo dpkg --configure -a

Then type in your password.

---

### Post by csf111 on 2007-04-30
...are you saying SUDO dpkg --configure -a

---

### Post by oilchangeguy on 2007-04-30
wormser
Location: Redmond, WA

Bill is that you?

---

### Post by silentjudas on 2007-04-30
irony...i use sudo for EVERYTHING and the one time it's obvious....it's obvious...

---

### Post by wormser on 2007-04-30
Wow, you are the first to notice my location and no I am not Bill.  I lived my whole life just down the street from m$.  I hate how people refer to them as Redmond... its a nice place to live and they make it sound like the devil's layer.

---

### Post by oilchangeguy on 2007-04-30
just messing with you. 
windows is an ok os. people who have problems with it, or any os for that matter, bad mouth it. rather than trying to fix the problem.

---

