---
title: "Beryl not installing"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Gigzaholic on 2007-06-18
installed all of its dependencies, I updated all of the gpg security keys, I deleted a few things related to compiz (now that I look back, maybe it wasn't a good move?), and I'm using these directions to install beryl: [http://wiki.beryl-project.org/wiki/Install...Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install...Feisty_with_XGL)

I tried to install it through the terminal and synaptic. Both of these methods failed. Here's a screenshot of the error I get:
[IMG]http://img377.imageshack.us/img377/1904/screenshot1jb6kq6.png[/IMG]

---

### Post by Ozeuss on 2007-06-18
I don't know if it helps, but it seems to depend on the packages heliodor, libberylsettings0-gconf, and beryl. it conflicts with beryl-defaults, and beryl kubuntu. maybe you should try to install the beryl package first.

---

### Post by Gigzaholic on 2007-06-18
some of those dependencies won't install because they also have dependencies. There's got to be an easier way man.:(

---

### Post by starcraft.man on 2007-06-18
> **Gigzaholic said:**
> some of those dependencies won't install because they also have dependencies. There's got to be an easier way man.:(

Ok... gah. I don't see anything at all on the page you linked to. You do not need that package you tried to install in the SS, the core applications you need to install and run Beryl are the following:

```
sudo apt-get install beryl beryl-core emerald-themes beryl-manager beryl-plugins-data beryl-plugins 
```

To install the unsupported (optional) plugins install these plugins:

```
beryl-plugins-unsupported beryl-plugins-unsupported-data 
```

Can you please tell me what card your installing on? I assume its either ATI or NVidia, please be sure that you installed your graphics drivers, if not use [Envy.]("http://albertomilone.com/nvidia_scripts1.html") If you've already done that skip that step and follow this guide on Ubuntu guide:

[Nvidia with aiglx]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28Nvidia.29")
[[URL="http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29"]ATI with XGL]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#What_to_do_if_Video_players_crash_while_using_Beryl")
Do this fix if video players crash when using Beryl (doesn't hurt to do it anyway).[/URL]

Remember that while Beryl is nice, it isn't 100% stable (I don't crash often at all). If you have any trouble don't be shy.

---

### Post by Gigzaholic on 2007-06-18
Ah crap, the link to the guide I was previously using isn't working. Ah well. Anyways I'm using an nvidia 6600. Basically I just want that 3d cube desktop and the "swishy" windows thing. Someone recommended that I should set-up beryl for that. 

Also aren't xgl and beryl the same thing? If they are different, can you please explain the difference?

Edit: I get what "sudo" is, but what is "gksudo?"

---

### Post by irish_flu on 2007-06-18
Beryl USES xgl to display its graphics.  You need XGL to use Beryl (I think).

gksudo is "sudo" for graphical applications (applications that run within Gnome/Xwindows).  I can't remember exactly why, but I've been warned many times that using regular sudo to fire up GUI applications will eventually screw something up.

please note: "screw something up" is a technical term.  :p

---

### Post by Gigzaholic on 2007-06-18
I just installed beryl. Looks pretty nice. Lol, It's what Aero tries to be but FAILS! 

Btw- do you know which command you have to use to get the whole picture of the 3d cube?

---

