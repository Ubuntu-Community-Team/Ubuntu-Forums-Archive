---
title: "[SOLVED] Which ubuntu distro to choose?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by IgnoranceIsBliss on 2007-11-06
Hello everybody,

I'm curious to know which Ubuntu distro i should use, here are my requirement:
[LIST]
[*]Dual processors, 64-bit environment.
[*]I really like the KDE desktop environment.
[*]I need occasionally to test some development on a ~LAMP server, but i'd like the daemons to be turned off on a general basis:
[LIST]
[*]Apache
[*]MySQL, PostGreSQL and SQLite
[*]PHP 5
[*]mod-perl
[*]PostFix
[/LIST]
[*]Additional languages: French, German and Italian.
[/LIST]
Basically that's it, to turn on or off the daemons, i can make a script, and handling the various installation procedures isn't a problem... In fact what i really need is a clarification about which distro does what. For example:
[LIST]
[*]I install ubuntu, then
[LIST]
[*]install kubuntu-desktop
[*]install various ~LAMP servers
[*]language-packs
[/LIST]
[*]install ubuntu-server
[LIST]
[*]install other various the various ~LAMP servers
[*]intall kubuntu-desktop
[*]language-packs
[/LIST]
[*]install kubuntu
[LIST]
[*]install various the various ~LAMP servers
[*]language-packs
[/LIST]
[/LIST]
What i'm not sure about is: does these various way to install guarantee me to end up with the same install? Or is there a preferred way to proceed?

---

### Post by kebes on 2007-11-06
> **IgnoranceIsBliss said:**
> What i'm not sure about is: does these various way to install guarantee me to end up with the same install? Or is there a preferred way to proceed?

Yes, you will end up with (more or less) the same final system with those different installations routes. However, the "server" edition is somewhat more optimized for being a full-time dedicated server (instead of a desktop machine). Also, if you install Ubuntu (then kubuntu-desktop) you will have a whole bunch of Gnome apps and libraries that you may not actually use (since you prefer KDE).

So, your best option is the third one: install Kubuntu (64-bit desktop version). You can then very easily app a LAMP setup (just install apache2, mysql, php), and add your language packs. This will give you the best system without anything you don't need.

---

### Post by LowSky on 2007-11-06
if you want KDE, then download Kubuntu, Kubuntu will not install any part of Gnome at all.l

---

### Post by Inxsible on 2007-11-06
The server edition will NOT have a GUI. So if you want a GUI, then you would have to download the Desktop version. 

So you have only one choice now
[Kubuntu]("http://kubuntu.org/download.php")

---

### Post by IgnoranceIsBliss on 2007-11-06
Wow, kudos to you all for such quick replies... And thanks for guiding me, so it looks like the best way to go is:
[LIST]
[*]Install KUbuntu
[LIST]
[*]Install various ~LAMP servers
[*]Install language-packs
[/LIST]
[/LIST]
Thanks again, I appreciate your help a lot.

---

### Post by Inxsible on 2007-11-06
you are welcome.

Please mark you thread as solved. (Thread Tools>>Mark Thread as solved)

---

### Post by IgnoranceIsBliss on 2007-11-06
Inxsible: done. I didn't knew threads were having a status... I should lurk here more often... :)

---

