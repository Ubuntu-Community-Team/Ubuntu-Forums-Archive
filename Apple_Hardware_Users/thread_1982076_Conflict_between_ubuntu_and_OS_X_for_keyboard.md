---
title: "Conflict between ubuntu and OS X for keyboard?"
date: 2012-05-17
forum: Apple Hardware Users
---

### Post by Lunarts on 2012-05-17
Hello, I managed to install and boot ubuntu on my imac 2011 computer using rEFInd, super grub 2 disk and a wacom tablet(all I had resembling an usb mouse), very tiresome process. The great last problem(I hope) I'm facing regarding ubuntu on mac is:

1 - When Ubuntu finally have the apple keyboard and mouse working(thought OS X has lost it all), at the mac pre boot screen(where the apple keyboard is turned on) the computer seems to had lost control over the keyboard wake up process, and as such, I cannot change the OS I want to boot at rEFInd(no keyboard input), neither can I use alt and C pre boot hotkeys on mac.

2 - When mac OS X itself has control over the keyboard and mouse, ubuntu doesn't have it; thought pre boot hotkeys and keyboard input works, indicating which maybe OS X has some control over the pre boot keyboard wake up process.

3 - Currently I'm stuck at ubuntu as ubuntu was the last system to seize control of the keyboard and mouse, and the first entry at rEFInd.

Basically I could only get one OS to have keyboard input, never both OS's. So, anyone know about a fix for that? Thanks for any help.

---

### Post by Lunarts on 2012-05-18
The only workarounds I can see for that are:

1 - Somehow get write acess to the OS X partition and make rEFInd always boot from OS X: I would have pre boot keyboard, so would be able to most of the time enter Ubuntu, and if no keyboard was present after ubuntu acess, pairing the keyboard at OS X would solve any keyboard lockup.

2 - Maybe editing ubuntu grub somehow can enable keyboard acess, then I would be able from Grub 2 menu to select OS X anytime I wanted.

3 - Edit grub to always boot mac OS X, due to the fact which OS X seems to be important for pre boot keyboard pairing; from there I could fix rEFInd default entry and restore ubuntu grub to its default behavior(otherwise rEFInd ubuntu entry would always boot OS X)

If anyone have hints about how could I achieve one of these two options, or have a better idea, let your idea be heard now.

---

### Post by Lunarts on 2012-05-19
Sorry for the delay, I was busy panicking due to the fact I edited grub 2 to boot the mac OS X entry which was number 7; guess what, I should had put 6(grub also counts 0, so 7-1 = 6), due to that mistake I was forever bound to load ubuntu as there was no apple keyboard wake up at startup, and ubuntu failing due to that wrong grub entry number.

I had to spent some cash to get an usb keyboard and reinstall ubuntu, as fixing the grub entry number from live cd didnt worked. To make my day I discovered which a clean ubuntu install with just EFI grub and blueman(which is unlikely to influentiate boot) lead to useless and unstable OS X boot entries(there are two entries) at grub menu; so I was already doomed when I didnt set rEFInd default menu entry to OS X(entry 2) right after ubuntu install, so apple keyboard always worked at startup(and if not, OS X would pair it again)

so for all means and purposes, ubuntu 12.04 will be useless to you without at least an usb mouse(or graphic tablet), you will have to everytime you pass from one OS to another to pair the mouse and keyboard; and if you do not do that rEFInd entry fix soon enough you WILL need an usb keyboard, so I recommend having one for now.

---

### Post by pbhedlund on 2012-05-19
The bluetooth issue is discussed here [http://ubuntuforums.org/showthread.php?t=1874245](http://ubuntuforums.org/showthread.php?t=1874245) and here [http://ubuntuforums.org/showthread.php?t=1980171](http://ubuntuforums.org/showthread.php?t=1980171).

I plan to file a bug report as I have not found one yet. If you beat me to it, that's fine.

---

### Post by Lunarts on 2012-05-19
Here it is: [https://bugs.launchpad.net/ubuntu/+bug/1001825](https://bugs.launchpad.net/ubuntu/+bug/1001825)

I hope it isn't like my bug report about my previous HP touchsmart computer, where the bug report was more like a loss of time(no true fix was ever proposed); or one of those bugs which take ages to be solved.

---

### Post by Lunarts on 2013-02-10
A person at launchpad said he found a good solution for this issue, I cannot test that now, but if you want to help you could enter [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1001825]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1001825") and give a try at the last hint(I guarantee nothing) and report there your findings.

---

