---
title: "PANIC: Feisty to Gutsy upgrade Xorg Broken!"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by vertexoflife on 2007-09-24
Yeah, I was stupid and upgraded to gutsy...even when it all said I shouldent exactly do it.

How can I revert to Feisty or fix my gutsy to work? 

When I boot up it says that Xorg could not be configured correctly I got the impression from Launchpad that it has something to do with the Intel chip. Are there any solutions to the problem?

Toshipa Tecra laptop...

---

### Post by splintercellguy on 2007-09-24
Yeah, an upgrade to Gutsy wasn't a good idea. Have you tried doing sudo dpkg-reconfigure xserver-xorg?

---

### Post by vertexoflife on 2007-09-24
> **splintercellguy said:**
> Yeah, an upgrade to Gutsy wasn't a good idea. Have you tried doing sudo dpkg-reconfigure xserver-xorg?

Xserver.org is apparently not installed.

---

### Post by vertexoflife on 2007-09-24
And apparently it is not a package to get anything? apt-get install xserver.org does not work for me.

---

### Post by vertexoflife on 2007-09-24
This is what I get from launchpad. But it dosent seem to apply to me 

> If you change intel to i810 then the problems go away. Work Around listed below

1. Wait for pc to boot to desktop for the first time
2. Press Alt+Ctrl+F1
3. At the prompt type in your username and then your password or on live cd ubuntu then hit return
4. Type in sudo nano /etc/X11/xorg.conf
5. Press the down arrow until you get to the line that says Driver "intel"
6. Change the word intel to i810
7. Press Ctrl+x, then y, then return to save and exit
8. Press Alt+Ctrl+F7 When the screen appears hit Alt+Ctrl+backspace to restart the Xserver

my /etc/X11/xorg.conf  already says "i810'

---

### Post by vertexoflife on 2007-09-24
Going to go get some food, been working at this problem a long time. lol. I will be back in ten minutes..

---

### Post by Adramelech on 2007-09-24
btw you should check your logs, thats the first thing to do

---

### Post by vertexoflife on 2007-09-24
How should I do that?

---

### Post by vertexoflife on 2007-09-24
Is it possible to maybe reinstall feisty again? Downgrade, if you will?

I'm actually on my roomates computer..he's waiting for Halo  3 to come out... =P

---

### Post by splintercellguy on 2007-09-24
Sure, why not? Just make sure to backup your fine /home. As for checking logs, dmesg or cat /var/log/Xorg.0.log?

---

### Post by vertexoflife on 2007-09-24
How do I back up /home in terminal? And how to reintall feisty over Gutsy?

---

### Post by Adramelech on 2007-09-24
nano  /var/log/Xorg.0.log to check you Xorg log

Reinstall as usual, boot on live cd and install.

To make the backup is better to use the livecd, copy your whole home directory to a external drive using nautilus, that way you avoid the terminal.

---

### Post by vertexoflife on 2007-09-24
I cant copy everything but /cat gives me a bunch of stuff and then 
Fatal server error: no screens found

---

### Post by vertexoflife on 2007-09-24
Oh god...there's no way I'm gonna be able to get a live CD before tomorrow morning. lol. ****.

---

### Post by vertexoflife on 2007-09-24
Once again the nano gives me a bunch of stuff then no drivers avaiable and no screens found.

---

### Post by Adramelech on 2007-09-24
We really need more lines to help, try pasting more lines.

---

### Post by vertexoflife on 2007-09-24
I cant paste but I can try to transcribe..umm give me a bit.

---

### Post by vertexoflife on 2007-09-24
protocool version 11 Release 7.2
Then there is a bunch of stuff about fonts.
Then ABI version information
Loads pcidata and displays a bunch of hex.
Talks about Intel Bridge and gives a bunch of info about that.
PCI and system report ranges.
Loads Extensions...
These are the last lines

(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor= "The XFree86 Project"
compiled for 4.2.0, module version 1.0.0
Module class: XFree86 XInput Driver
ABI Class: XFree86 XInput Driver, version 0.3
(EE) No drivers available.

Fatal server error:
no screens found.

---

### Post by vertexoflife on 2007-09-24
Anyway to downgrade from gutsy to feisty in terminal?

---

### Post by Adramelech on 2007-09-24
maybe changing the gutsy word for feisty in your source list but im afraid thats gonna broke everything else.

You should try reinstalling ubuntu-desktop

sudo apt-get --reinstall ubuntu-desktop

---

### Post by vertexoflife on 2007-09-24
This is for everyone else: Don't try reinstalling ubuntu desktop, it just got done and I rebooted and now I have no command prompt sat all and I cant rescue files.

---

