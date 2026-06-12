---
title: "Flash videos and Ubuntu"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by CBTF on 2006-08-04
Today I installed automatix, and it was supposed to have put the flash plugin on my computer. Despite this, I am unable to view flash movies (youtube, newgrounds etc.)

In firefox the flash window appears empty white, and nothing loads.
In mozilla browser i'm told I don't have the plugin.

What's up?

---

### Post by cantormath on 2006-08-04
> **CBTF said:**
> Today I installed automatix, and it was supposed to have put the flash plugin on my computer. Despite this, I am unable to view flash movies (youtube, newgrounds etc.)

In firefox the flash window appears empty white, and nothing loads.
In mozilla browser i'm told I don't have the plugin.

What's up?

I installed flash for firefox with automatix, and it works great.
I installed 
looking in my automatix log I install


MPlayer & FF plugin|Network Manager
Debian Menu
Extra Fonts|NDISWrapper
Flashplayer
SUN JAVA 1.5 JRE|Swiftfox Browser|Swiftfox Plugins
Swiftfox Plugins
XChat
RealPlayer|Ripper and Tuner


see if installing those some of those aid you in your quest.  Of course, you dont need everything there.  But the Players, plugins, Mplayer with FF plugins and maybe swiftfox with plugs might help

---

### Post by CBTF on 2006-08-04
ive got all of those installed as well.. im still unsure what could be causing this (i know nothing about linux either, so its hard to muck around)

---

### Post by Jagot on 2006-08-04
Providing you have the package flashplugin-nonfree installed (check in Synaptic), try running the following command:

```
sudo update-flashplugin
```

---

### Post by CBTF on 2006-08-04
"Providing you have the package flashplugin-nonfree installed (check in Synaptic), try running the following command:"

I do not see flashplugin-nonfree in synaptic.

"sudo update-flashplugin"

Which would be why this doesnt work :(

im clueless, what now?

---

### Post by CarpKing on 2006-08-04
Did you enable the extra repositories in Synaptic?

---

### Post by cantormath on 2006-08-04
> **CarpKing said:**
> Did you enable the extra repositories in Synaptic?

you could start automatix,
then when its open, run that command.....
sudo apt-get install update-flashplugin

once its installed, closed automatix and click yes to restore repositories.

another way to do it is to change your source list.....

System>Administration>Software Properties
add the Universe repos
or
sudo gedit /etc/apt/sources.list 
and un comment the repos you need, im guessing universe.
then
sudo apt-get update
sudo apt-get install update-flashplugin

Thing is, if you do it that way, you got to go back and change the repos it back.

---

