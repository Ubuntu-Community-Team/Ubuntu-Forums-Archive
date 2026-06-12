---
title: "I install some games but they dont show up in the Games menu."
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by jkensil on 2006-08-30
So Im trying to install some games. Some have successfully installed and I am able to see them under Applications-> Games, but some have not. Just wondering why or how I can get these to show up. According to Synaptic theyre already downloaded and installed.](*,)

---

### Post by xpod on 2006-08-30
Try using your "alcarte menu editor" or you can press alt+f2 and type it`s name in or you can type it at a terminal.....you`ll find the actual terminal commands in synaptic i think.

Or get the debian menu..THATS good for showing all apps on pc.

---

### Post by TFX360 on 2006-08-30
> **jkensil said:**
> So Im trying to install some games. Some have successfully installed and I am able to see them under Applications-> Games, but some have not. Just wondering why or how I can get these to show up. According to Synaptic theyre already downloaded and installed.](*,)

Dear jkensil,


I sometimes have the same problem. Most of the time I make my own icon after a locate under terminal. Probably just bugs. If someone has a better answer I'll be glad to hear.

---

### Post by ewl1217 on 2006-08-30
The reason some programs wont show up in the menu is because they don't come with freedesktop.org (I think...) compliant menu entries. You can manually add them to the menu, launch them from the terminal, or, as xpod said, install the Debian menu (which shows all programs).

---

### Post by dchglat on 2006-08-30
Open the terminal and try running the program. For example, if you're trying to run the program xpenguins you'd simply type "xpenguins" into the terminal; nothing else. If the program runs, then it *is[I]*[/I] installed and all you need to do is open your start menu and right click somewhere in it. You should be given the option of "edit menu" or something like that. I'm not using ubuntu right now but I'm sure it'll have something similar. There you can add a shortcut under games/amusements and where it asks to enter a command, type "xpenguins" or whatever the name of the program is.

---

### Post by TFX360 on 2006-08-30
I definately cannot tick the Debian menu in Alacarte. Wierd huh!


[IMG]http://home.casema.nl/d.sluijter/Alacarte.png[/IMG]

---

### Post by jkensil on 2006-08-30
Alt + F2 worked for some but not all. 

Ex. I installed "battleball" via Synaptic. Went and did F2 and typed battleball and never got a thing.

---

### Post by comppsyco on 2006-09-01
How does one install the debian menu?

---

### Post by jordanmthomas on 2006-09-01
first, enable multiverse and universe repositories (you probably already have since you're installing games)

Just in case you don't know how....[here]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories")

```
sudo apt-get update
sudo apt-get install menu
```

---

