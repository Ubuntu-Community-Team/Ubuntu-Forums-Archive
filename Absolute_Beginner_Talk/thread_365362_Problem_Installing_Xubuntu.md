---
title: "Problem Installing Xubuntu"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by drakonis314 on 2007-02-19
I'm trying to install Xubuntu on an old Compaq with 128M RAM and a 6MHz processor.  I start the computer and insert the Xubuntu 6.10 ISO CD.  A screen will come up giving me 6 different choices and I select run or install Xubuntu.  It will install the kernel and come to a desktop screen with two icons on it, Examples and Install.  I'll left-click on install and select 'execute'.  After a few minutes a window will pop up.  It's a blank white window with Install in the header.  The install process stops there and the computer freezes up.  What do I need to do to complete the install?

---

### Post by taurus on 2007-02-19
Why not use the alternate version to install it on your machine?

[http://ubuntu-cdimage.datahop.it/xubuntu/releases/6.10/release/](http://ubuntu-cdimage.datahop.it/xubuntu/releases/6.10/release/)

p.s.  6MHz processor!!!

---

### Post by lyceum on 2007-02-19
The live CD needs 256mb or RAM to work, even for Xubuntu. Once you get the PC working with the alt instal cd, it will run with what you have. You may want to throw some more RAM in though, if you can. :)

---

### Post by drakonis314 on 2007-02-19
Hehe, sorry, 600Mhz processor.

I used the Alternate Install first, but there doesn't seem to be a GUI and I don't know enough about the text commands to use it properly.

---

### Post by taurus on 2007-02-19
It is real easy even in text mode.

---

### Post by Brendantb on 2007-02-19
Hi, Drakonis, 

You don't need to know anything about text commands, you just have to follow the on screen instructions. 

You may have to use the arrow keys to manoeuvre the red highlight onto the right option. 

It doesn't take that much longer than the live CD either.

---

### Post by drakonis314 on 2007-02-19
I've already gone through the complete intallation using the alternate install CD but all it gives me is a command line interface and I'm trying to set this computer up for use by my friend's four-year-old so he doesn't wreck the family's main computer.  Is there a GUI for the alternate version of 6.10 or should I give up on this computer and try one that has a little more memory?

---

### Post by taurus on 2007-02-19
Did you pick the first option on the menu to install from the alternate CD?

---

### Post by jvc26 on 2007-02-19
Thats odd as when I use the alternate cd it gives me a text based install - not a CLI one - its a step by step thing... - did you boot with the first option?
Il

---

### Post by drakonis314 on 2007-02-19
I honestly don't remember.  Looking at it now I see four install options, Text, OEM, CLS and LTSP server.  Is there a preferred one?

---

### Post by Brendantb on 2007-02-19
Hi, 

The end result of using the live or alternate install is the same. You should boot up to a GUI Login screen. 

You might want to try putting in "startx" at the prompt to see if it starts up the GUI, but this shouldn't be necessary really, though I had to do this with a Zenwalk installation, also with the Xfce desktop.

---

### Post by taurus on 2007-02-19
I think you probably have picked the last option, server.  You need to pick the first option, Text, to install it.  Text means install XFce4 in a text mode.

---

### Post by taurus on 2007-02-19
> **Brendantb said:**
> though I had to do this with a Zenwalk installation, also with the Xfce desktop.

You just have to edit /etc/inittab and change the value from 3 to 4 in Zenwalk for it to boot into GUI login screen.

---

### Post by crimesaucer on 2007-02-19
I think the text mode is the easiest. This page has really good instructions for a dual boot of Windows Xp, and a FAT32 partition to have for file transfer between the two. I used it for my xubuntu edgy install: [http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm)

Search around his homepage menu for many more links about installing: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

