---
title: "[SOLVED] Kubuntu feisty alternate get stuck during installation"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by zxccvb on 2007-07-24
I'm trying to install feisty on my lappy using the alternate cd, but it keeps failing on me.

It basically get stuck at some point and freeze during the installation. Once was at 68%, once a 81. I tried using Ctrl-Alt-F2 to go to a console, but the first time the consoole was dead too, the second time i was able to kill a random process but it basicakky screwd everything up and i had to reset.

BTW I have an acer laptop with 1.5 Gb of RAM and a X700 ati gpu.

Is this a known problem? Any known solution?

EDIT: i checked the CD for defects and it has none. So it's not the cd.

---

### Post by hyper_ch on 2007-07-24
You say it has no defects... so I assume that to be true ;)

well, on a very rare occasion the alternate cd does not work for install (e.g. my mom's computer)... you might be better of trying the desktop cd for installation...

---

### Post by zxccvb on 2007-07-24
I was avoiding it because on past installation (edgy and the one before) the mainstream cd didn't work at all.
I guess because of issues related to either the ati card or the acpi or both.

Translated into human language all that means that all i was able to get get was just a black screen. :lol:

I might try the mainstream cd but knowning his bad history with my lappy i'm not overly confident about it.

---

### Post by hyper_ch on 2007-07-24
Or you could try another alternate cd like the xubuntu or kubuntu one... maybe those help.

---

### Post by zxccvb on 2007-07-24
Yeah maybe. 

BTW i tried again and it got stucket at 85% with a "Installed brltty-x11" as label.

I looked around for it and found this guy ( [http://ubuntuforums.org/showthread.php?t=449166](http://ubuntuforums.org/showthread.php?t=449166) )had the same problem and end up solving it waiting more than two hours!!! 



This sucks big time. >[

---

### Post by mjwhitfield on 2007-07-24
Can I suggest trying the minimal CD? then downloading the packages you need after the install?

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by zxccvb on 2007-07-24
SOLVED. I Just had to wait about a hour. 

I think there's some issue here.
It really seems frozen and i think it takes an awfull amount of time to do what it does.
I mean what's the point of having a progress bar if it runs from 0 to 85% in a blink and then got stuck on it for an hour on the same thing.  It sure doesn't give the impression that everything is fine and working.

Anyway it seems that all you have to do is just to sit back and be patient :popcorn:

Thanks for your helps.

---

### Post by tonyrav on 2007-10-12
The same thing happened to me too when installing with the ubuntu alternate CD on my laptop. What I did was I've used ALT-F2/F1 to navigate back and forth from the install console to the command prompt.
After getting the prompt #.. I cd'd to the /cdrom just to be curious if I could browse the cd-rom and all of a sudden the cd-rom started spinning again..so I pressed ALT-F1/F2 again to get back to the installation console and the installation continued again and finished ok!
It seems to me that the cd-rom is getting "asleep".. weird!! ;-)...But it worked for me..
...Good luck to you guys..

Tony.

---

### Post by oucii on 2007-12-05
I was installing alternate cd with VMware Worstation, and loaded the iso image from the hard drive, got stuck at 85% "installed brltty-x11 too" so it's not a cd-rom problem, weird. Yes it did continue the installation, after a long while, but definitely not 2 hours, erm, 25 mins.

---

