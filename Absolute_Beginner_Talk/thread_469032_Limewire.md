---
title: "Limewire"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by tdaman927 on 2007-06-09
i was installing limewire, it froze so i rebooted and now i get this message when i try to install agian

[IMG]http://i124.photobucket.com/albums/p11/tylerhopp/Screenshot.png[/IMG]

---

### Post by Outrunner on 2007-06-09
Go to System-> Administration-> System Monitor(I think that's the name, I'm not using Gnome right now) andd kill any APT based programs(Synaptic etc...)

---

### Post by tdaman927 on 2007-06-09
im not sure wat u mean by "kill any APT based programs(Synaptic etc...)"  i looked in to that before and couldn't find anything that would do anything that would aloow me to open the Synaptic package manager

---

### Post by Outrunner on 2007-06-09
Are you sure? Can you post a screenshot of the System Monitor menu?

Anyway, this is also worth a try, but I'm not entirely sure it will solve your problem

```
sudo dpkg --configure -a
```

---

### Post by tdaman927 on 2007-06-09
that works thanks so much but now i go to install AGAIN and it will freeze at this
[IMG]http://i124.photobucket.com/albums/p11/tylerhopp/Screenshot-2.png[/IMG]

---

### Post by Outrunner on 2007-06-09
Sorry, I almost laughed out loud you know! :D You simply have to press and hold enter until it asks you if you agree(then type yes and press enter)

---

### Post by tdaman927 on 2007-06-09
thank i feel dumb now its installed and works great

Tyler

---

### Post by Outrunner on 2007-06-09
Don't worry I made this mistake too the first time I was installing java

---

