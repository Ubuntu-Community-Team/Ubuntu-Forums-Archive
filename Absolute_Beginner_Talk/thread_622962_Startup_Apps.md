---
title: "Startup Apps"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Spoken on 2007-11-25
im using gutsy 7.10, and i know this is a really lame question, but for the life of me i cant find where i can select what runs on boot rather then having to manually run something after boot.:lolflag:

---

### Post by Taboo Mirage on 2007-11-25
If you're talking about wishing to run an application graphically after you login as a user, then see System > Preferences > Sessions and see the "Startup Programs" tab.

---

### Post by Spoken on 2007-11-25
ok yea, thats what im talking about. i found that part, now my new problem is, what is the command that i use? im trying to make my Avant Window Navigator run on startup, but i dont know the command lol

---

### Post by Taboo Mirage on 2007-11-25
If you enter this into a terminal:

```
avant-window-navigator
```

It should start it, I believe.  If it does, that'll be the command you're looking for. ;)

---

### Post by toupeiro on 2007-11-27
you will find that many applications in linux start by name in a terminal.  do not be afraid to try some.

examples:
```

firefox
totem
amarok
pidgin
gimp

```
in the case of applications with multiple words in the name, like avant window navigator, are connected by dashes (-) or underscores ( _ )  like:

```
avant-window-navigator
```

or 
```

gnome-system-monitor

```
If you want these applications to simply 'start' in the terminal and have the terminal available to start more applications, put a & at the end of the command.

e.g. 
```

avant-window-navigator &
```

also, most importantly, using the <tab> button on your keyboard in a terminal window will auto-complete your typing of any 'known' command or file in the system.  
for example, if you typed: gnome-system-m<tab>  it would finish the name of the command to completion. 

if there were multiple files that shared the same part of a name, it will auto complete up until the point that the name was the same, then you have to give it the next few characters of the file to identify the file you want from what is available.

e.g. if you type ```
gnome-syste<tab>
```  
you will likely have two choices:

gnome-system-log 
and
gnome-system-monitor

so, by typing ```
gnome-system-m<tab> 
``` 
linux now knows which file you are trying to execute. 

anything you can type in a terminal like this, you can put in your start programs tool in system | preferences | sessions.  Just be careful, or your startup will take as long as Windows. :)

enjoy :)

---

### Post by jordanmthomas on 2007-11-27
> If you want these applications to simply 'start' in the terminal and have the termal available to launch more applications, put a & at the end of the command.
Also remember that if you start the program this way, don't click the x on the terminal window to close it.  Close it by typing exit and then hitting enter (or you can press ctrl-d)

---

### Post by pao_03 on 2007-11-27
I just had kiba-docks installed and last instructions were same as the ones above, to go to system preferences and then sessions. I tried adding the kiba-dock command and clicking close... but does not work. When I open Sessions again it's as if nothing happened. 

Also tried this with other programs and nothing works, it reverts back to the original sessions, even tried unchecking blutooth to see if it would save my changes but still does not work. 

Also tried saving sessions when I close but when I restart nothing seems to be back up. Hope someone could help. Maybe I could try the manual way of adding to startup through the terminal or something, 

Thanks

---

