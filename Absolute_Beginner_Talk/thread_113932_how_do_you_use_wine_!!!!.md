---
title: "how do you use wine ?!?!?!?!?"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by djlilyazi on 2006-01-07
Hi,

i just want to some with wine i have nooooooooo clue how to use it...

is there a site that will help me or anythingggggggggggggggggggg

thanks

YAZ

---

### Post by etc on 2006-01-07
Ok
```
sudo apt-get install wine
```
to install from a terminal

or 

System -> Administration -> Synaptic Package Manager, to open a GUI.  Click search, type "wine", locate wine on the list, right click it -> select Mark for Installtion, then click apply.

After it installs, open a terminal and type **winecfg** to configure it.
Download your windows program, and save it somewhere
```
wine NAMEOFWINDOWSPROGRAM.exe
```
in a terminal
or in Nautilus, you could double click it, but I had varied results doing it that way.

---

### Post by djlilyazi on 2006-01-07
[QUOTE=etc]Ok
```
sudo apt-get install wine
```
to install from a terminal

or 

System -> Administration -> Synaptic Package Manager, to open a GUI.  Click search, type "wine", locate wine on the list, right click it -> select Mark for Installtion, then click apply.

After it installs, open a terminal and type **winecfg** to configure it.
Download your windows program, and save it somewhere
```
wine NAMEOFWINDOWSPROGRAM.exe
```
in a terminal
or in Nautilus, you could double click it, but I had varied results doing it that way.[/QUOTE]


thats it wine then name of prog and .exe... man u must be kidding ? wow

---

### Post by djlilyazi on 2006-01-07
[QUOTE=etc]Ok
```
sudo apt-get install wine
```
to install from a terminal

or 

System -> Administration -> Synaptic Package Manager, to open a GUI.  Click search, type "wine", locate wine on the list, right click it -> select Mark for Installtion, then click apply.

After it installs, open a terminal and type **winecfg** to configure it.
Download your windows program, and save it somewhere
```
wine NAMEOFWINDOWSPROGRAM.exe
```
in a terminal
or in Nautilus, you could double click it, but I had varied results doing it that way.[/QUOTE]

i want to use MIRC so i can get stuff from [www.ircspy.com](www.ircspy.com)

that is possibel right ?

---

### Post by aysiu on 2006-01-07
[QUOTE=djlilyazi]i want to use MIRC so i can get stuff from [www.ircspy.com](www.ircspy.com)

that is possibel right ?[/QUOTE] I don't really know what IRCSpy does, but have you tried enabling extra repositories (see the first link of my sig) and searching Synaptic (under Name and Description) for *irc*?

---

### Post by etc on 2006-01-07
Only way is to try it out and see.
The AppDB on [http://winehq.org](http://winehq.org) says that it should be fine
[http://appdb.winehq.org/appview.php?appId=77](http://appdb.winehq.org/appview.php?appId=77)

---

