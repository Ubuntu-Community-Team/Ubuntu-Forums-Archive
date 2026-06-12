---
title: "adding command to panel"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by thelegionnaire on 2007-07-25
so i have an external soundcard that i use for audio work in my studio, otherwise i just use the built in card in my laptop, i would like to add a button on the panel, that would send the command to switch from my built in soundcard to the usb, and another one to do the opposite, i would assume that you COULD do this in the terminal, so i was wondering what the command is for that, yes i know i can just go to prefrences/sound, i'd just really like a button on my panel

---

### Post by lisati on 2007-07-25
If you know which command(s) to put in you might be able to do something with right-clicking on the panel, clicking on "Add to panel" and then clicking on "Custom application launcher"

---

### Post by thelegionnaire on 2007-07-25
yeah thats what i want to do i was just hoping someone knew the commands

---

### Post by thelegionnaire on 2007-07-26
\\:D/ Bump bump

---

### Post by thelegionnaire on 2007-07-27
c'mon guys, nothing?

---

### Post by kmslinux on 2007-07-27
> **thelegionnaire said:**
> so i have an external soundcard that i use for audio work in my studio, otherwise i just use the built in card in my laptop, i would like to add a button on the panel, that would send the command to switch from my built in soundcard to the usb, and another one to do the opposite, i would assume that you COULD do this in the terminal, so i was wondering what the command is for that, yes i know i can just go to prefrences/sound, i'd just really like a button on my panel

Well, you could just drag the System -> Preferences -> Sound button on to your panel.

---

### Post by lambros on 2007-07-27
If it helps, you could have a look at the "alsamixer" command (you might have to install this package).

I've had a look at the man-page for alsamixer, and it seems you should be able to use the "-c" option to select which sound-card to activate.  So "alsamixer -c 0" ought to select one sound-card, "alsamixer -c 1" ought to select another, and so on.

Also, you could have a look at the "amixer" command.  Sorry I can't test this myself, as I only have one sound-card on my system.

Lambros

---

