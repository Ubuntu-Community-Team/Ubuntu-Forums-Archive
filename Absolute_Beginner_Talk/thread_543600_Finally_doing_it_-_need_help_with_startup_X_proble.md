---
title: "Finally doing it - need help with startup X problem and how to get online..."
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by jammadave on 2007-09-05
Hi guys, been thinking about it a couple weeks so I went for it - I have both WUBI and a LiveCD.  My setup is a Dell E1505 with the upgraded display.   Can't remember what the video card is.

First I tried the LiveCD, then WUBI... Both got me booting, but both hit a broadcom microcode failure, which I've read about here upon searching.   Apparently that has to do with the broadcom wireless card built into the computer....  But I don't use the wifi card, ever, so why would it be trying to configure it?   Can I just skip it to the desktop somehow, without needing to be online?  

(also why would a wifi issue affect the displaying of a GUI??)

I ask also because I assume I'm going to have a hard time getting my internet connection to work - I don't use the wifi in the computer at all, my only internet connections at home are via cellular Aircards, Novatel U720.   I have no hardline internet at my home whatsoever.  (I get the aircard for $15/mo and it's DSL speed, love it.)

So, for me to get running, I have the following questions in the order I think I should be getting them answered, so that I can then fix anything else that needs help.
[COLOR="Red"]
1.  How do I get around that broadcom microcode error, without being online?  (Note: I've not even *seen* the gnome desktop as yet because of this, so I suppose that is my goal.   As I don't need the wifi at this point, also, hopefully there is something i can do to ignore it for now.)

2. Also without being online, in order to *get* online, what do I need to do to install and configure the Novatel U720 - and do I need the Sprint software, somehow magically in Linux form, or is there something else specific that I would use for Ubuntu?

3. Once that is taken care of, with my setup (Dell E1505) will there be any limitations I'd need to get around, concerning the display drivers or anything else that is just a "core working function"?[/COLOR]

And of course, I know I'll need more advice later, but if there's anything I should do first or in between or what have you, please, let me know!!!

Cheers
Dave

---

### Post by bks on 2007-09-05
1.) What type of cardbus is it and can you just remove it from the computer?
2.) & 3.) Hmm...working on it.

---

### Post by jammadave on 2007-09-05
errrrr, I don't know what a cardbus is.   And as it's an internal wifi thing on the laptop I'm highly doubting I can remove it.

And thanks very much for looking and trying to help.

---

### Post by bks on 2007-09-05
2.) I found a webpage that may be of some use to you. As far as downloading any needed packages, I would use another computer and download them to some removable media and transfer the files that way.

Here's the [link]("http://samat.org/weblog/20070128-sprints-evdo-mobile-broadband-on-ubuntu-linux.html").

3.) I would cross that bridge when you get there.

---

### Post by bks on 2007-09-05
> **jammadave said:**
> errrrr, I don't know what a cardbus is.   And as it's an internal wifi thing on the laptop I'm highly doubting I can remove it.

Okay, for example on my laptop, there is a panel on the bottom that I can remove to expose my wifi card. It's not actually soldered to the board, it is connected through a socket. So if I needed to I could pull it out.  Flip your laptop over and see if there are any removable panels.  The card should have some labels on it, so it shouldn't be hard to identify. *Turn the power off, remove the battery and be aware of static*

---

### Post by anewguy on 2007-09-05
Here's one thing for you - the boot is detecting the wireless card and trying to use the built-in bcm43xx driver, hence the no firmware message.  To get rid of that message, try this:

- go to a terminal window (applications/accessories/terminal)
- gksudo gedit /etc/modprobe.d/blacklist
- go to the bottom of the file and add the following:

# default Broadcom driver, no firmware
blacklist bcm43xx

- save the file and exit
- reboot

However, if you want to get rid of the message and still have your wireless available at some point in the future, try this link - just go to the section (near the top) of getting wireless to work:

[http://ubuntuforums.org/showthread.php?t=507505&highlight=mx3215+how-to](http://ubuntuforums.org/showthread.php?t=507505&highlight=mx3215+how-to)

Welcome to Ubuntu - enjoy the experience!:)

---

### Post by jammadave on 2007-09-05
Hey new guy - your info sounds very helpful for getting rid of the broadcom problem - however, it assumes i can get to the terminal window and be online.   Therefore, I need to somehow get around the broadcom error, and into the X environment, and then get online with my aircard, before i can even attempt that.   Or, am I wrong?

Thanks so far guys...

---

### Post by jammadave on 2007-09-05
I'm really not understanding some of the methodology here - please forgive my ignorance...

- assuming i can download all needed package files, and create new ones needed; I can do this while i'm booted to windows and hopefully save to Wubi.  But where can i store them in the wubi directories, and in what format, so they can be found in the term window and then placed wherever?

- that said, if that doesn't work, is there anything i can do at the command line to force a skip to the desktop beyond that wifi card error, at least?

---

### Post by jammadave on 2007-09-05
> **anewguy said:**
> Here's one thing for you - the boot is detecting the wireless card and trying to use the built-in bcm43xx driver, hence the no firmware message.  To get rid of that message, try this:

- go to a terminal window (applications/accessories/terminal)
- gksudo gedit /etc/modprobe.d/blacklist
- go to the bottom of the file and add the following:

# default Broadcom driver, no firmware
blacklist bcm43xx

- save the file and exit
- reboot


OK, so I tried to do this, realizing it didn't involve downloading anything and I could force my way to a command line with ctrl alt f1.... but...

-Since the error stops X from starting at all, i can't use gksudo and gedit.
-when i try to just use sudo and edit, it gives me an unknown MIME-type error and looks like it tries to use " application/* " or something.
-when I try to find the file, it's not there.  Should I try to create it?  if so, what's the command?  (and what's the whole process for creating a file, putting content in, and saving, at the CLI?)

Thanks
Dave

---

### Post by jammadave on 2007-09-10
anyone have any further thought on my last post above?   Cause, I can't move forward at all with Ubuntu otherwise. =0(

---

