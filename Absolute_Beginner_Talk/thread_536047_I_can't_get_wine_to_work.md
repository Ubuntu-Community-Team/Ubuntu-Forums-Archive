---
title: "I can't get wine to work"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Liamkerrigan on 2007-08-27
Hello everyone, i just started using Ubuntu 7.04 my first Linux using ever. i don't know anything at all about it, i play world of warcraft and downloaded wine-0.9.44 i have absolutely no idea how to install it and because i have verry... very little knowladge of ubuntu and how everything works if someone could direct in the direction of a good tutorial or explain how to install it and get it to work with like step by step instructions. please help me all help greatly appreciated..

---

### Post by phyrewall on 2007-08-27
Here ya go:

[http://ubuntuforums.org/showthread.php?t=312482&highlight=warcraft+wine](http://ubuntuforums.org/showthread.php?t=312482&highlight=warcraft+wine)

Search button is your friend.

---

### Post by Hobo Joe on 2007-08-27
To install WINE: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

To install WOW on WINE: [http://ubuntuforums.org/showthread.php?t=312482&highlight=wow+wine+howto](http://ubuntuforums.org/showthread.php?t=312482&highlight=wow+wine+howto)
Warning though, this is pretty complex for a beginner.  Also, you need to be forwarned that WINE will not run any Windows app perfectly, lots of them will not work perfectly, and some will not work at all.

---

### Post by AndyCooll on 2007-08-27
Well to configure Wine you can type:
```
winecfg
```

However, Wine really sits in the background and simply kicks in "as an application layer" when you run a Windows program.

To get one to start you usually type something like:
```
wine name_of_program.exe
```

For WoW it's worth doing a search for a howto on these boards (I don't play the game myself but there are many on these boards who do).

Here's one to start you off: [URL="http://ubuntuforums.org/showthread.php?t=312482"]HOWTO: Play World of Warcraft under Ubuntu using Wine
[/URL]

:cool:

---

### Post by Liamkerrigan on 2007-08-27
Hobo Joe i went onto Wine HQ followed the instructions entered everythiing in teminal and then did 

sudo apt-get install wine

and it said Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)

what does this mean?

---

### Post by AndyCooll on 2007-08-28
The easiest way to get wine is to use the one in the repos. No need to get it from the Wine website (unless you really must have the most upto date version).

Just type Wine in Add/Remove programs or do a search in Synaptic, or in the command line type the following:

```
sudo apt-get install wine
```

:cool:

---

