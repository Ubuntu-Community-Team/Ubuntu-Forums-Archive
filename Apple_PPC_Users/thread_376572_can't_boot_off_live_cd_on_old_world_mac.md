---
title: "can't boot off live cd on old world mac"
date: 2007-03-05
forum: Apple PPC Users
---

### Post by scoper on 2007-03-05
hey

i have an old old imac, one of the first ones (it's 233 MHz, that greeny colour, that's about all i know. 94mB of ram or something if that sounds right)

anyway i downloaded ubuntu-6.10-desktop-powerpc.iso and burnt it to a cd and then booted into it on the old mac. i pressed enter at the "boot: " screen as you would, it came up with the ubuntu picture and a status bar. it filled that up then went to a flashing "_" in the corner. and the cd rom keeps making reading sounds. it sits there for about an hour doing nothing, by then i got bored and tried again but still the same thing. the screen goes to sleep a minute or two after the flashing _ appears and i can't press any keys or anything to try get a picture

what is going on ? am i doing something wrong ? or does it really take over one hour to load

thanks

---

### Post by 3rdalbum on 2007-03-05
1. iMacs are Newworld Macs.

2. This is a known bug - when the screen "goes to sleep", that's when Xorg starts, and it starts with the wrong monitor settings. If you press Control-Option-F2 when that happens, the monitor will switch back on and you will get the text terminal display.

Here's a thread that says what to do after that happens: [http://www.ubuntuforums.org/showthread.php?t=75604]("http://www.ubuntuforums.org/showthread.php?t=75604")

---

### Post by didg on 2007-03-05
If you really have only 94MB of RAM if afraid it's hopeless for the live CD, even Xubuntu won't run.

---

### Post by scoper on 2007-03-05
oh, sorry a new world.

wouldn't you think that the cd would stop reading even if it went to sleep? oh well, i'll give it a go after work


yeah 94 meg sounds small, but does it sound right? that's what it said in the system profiler bit i didn't believe it

---

### Post by 3rdalbum on 2007-03-06
94 megabytes sounds very irregular, but 96 megabytes isn't hard to believe - my Mac used to have 96 megabytes.

Xubuntu is probably out of your system's grasp without a memory upgrade. If all you wanted was a Linux-based server, then you could install Ubuntu Server, but that does not include a GUI.

---

