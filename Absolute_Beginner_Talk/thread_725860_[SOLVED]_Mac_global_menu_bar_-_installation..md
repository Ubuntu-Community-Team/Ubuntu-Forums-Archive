---
title: "[SOLVED] Mac global menu bar - installation."
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by lover_of_sc on 2008-03-16
Hi there,

I tried to follow the installation instructions on:

[https://wiki.ubuntu.com/global_menu](https://wiki.ubuntu.com/global_menu)

but I got lost halfway trough.. :-)

How do I install the menu in the easiest possible way? Thx

---

### Post by lover_of_sc on 2008-03-16
Ops I managed to do more damage then i though - when I go into the synaptic manager I get following error message: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


nooooo

---

### Post by banewman on 2008-03-16
You can fix that by opening a terminal and typing -
sudo dpkg --configure -a
:)

---

### Post by ferdostar on 2008-03-16
> **lover_of_sc said:**
> Ops I managed to do more damage then i though - when I go into the synaptic manager I get following error message: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


nooooo

1) Do what it says ;) run in Terminal 

```
dpkg --configure -a
```

2) Then you can take a look at [this how-to]("http://ubuntuforums.org/showthread.php?t=385981") from reacocard

---

### Post by lover_of_sc on 2008-03-16
Aw that worked, puh. :-)

This is embarrassing but here you go.

I managed to get the aviant windows navigator to show, but how do I add or remove anything from the menu? When I right click I get the option for 'preferences' but nothing happends when I click it?

---

### Post by lover_of_sc on 2008-03-16
I get this info in the terminal if that helps:

anders@anders-laptop:~$ avant-window-navigator &
[1] 6365
anders@anders-laptop:~$ Screen is composited.
APPLET : /usr/lib/awn/applets/taskman.desktop
Failed to execute child process "awn-manager" (No such file or directory)

anders@anders-laptop:~$ awn-manager &
[2] 6368
anders@anders-laptop:~$ bash: awn-manager: command not found
Failed to execute child process "awn-manager" (No such file or directory)

---

### Post by ferdostar on 2008-03-16
Maybe you can try with:

```
 sudo apt-get install avant-window-navigator awn-manager
```

---

### Post by lover_of_sc on 2008-03-16
Yes! That worked. Cheers buddy. :-)

---

