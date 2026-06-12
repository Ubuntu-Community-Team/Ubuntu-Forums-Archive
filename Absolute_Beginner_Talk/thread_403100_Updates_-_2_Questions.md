---
title: "Updates - 2 Questions"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-04-06
1) Recently several folks lost the use of their microphones and/or sound as the result of something being sent in the software updates. Has any progress been made to locate and correct this? 

2) I regret downloading whatever update caused the no-mic problem in my computer. I don't want any more software updates that will cause any more problems. How do I stop the automatic reminder to load the updates? After un-checking the updates and clicking Close, how do I remove the icon, and stop Ubuntu from reminding me that those updates are available?

---

### Post by Happy_Man on 2007-04-06
No. 2 is a problem I also have. Any help on this?

---

### Post by userundefine on 2007-04-06
You need to remove update manager from your session.

system>preferences>sessions>startup programs

---

### Post by RichPicker on 2007-04-06
Remove it? What about necessary updates? That makes no sense. It's all or nothing? Can't select which updates to load and which to refuse?

---

### Post by userundefine on 2007-04-06
Uh, it's not like you're deleting the entire program from your computer.  You're just removing the notifier for auto-updates from your session, i.e., what programs you load when you log into Gnome.  And of course you can select which updates to download and which not to.  When you open the update manager, you can check or uncheck what you want.  But if you're looking for some magical "I want to download all updates that will not break and avoid all updates that will", then you're looking in the wrong area.  There is no such magical button.

---

### Post by pppetter on 2007-04-06
And I would actually recommend that you continue to install the upgrades, since it's very likely there will come a fix for the things you mentioned - and don't forget al those security fixes.

---

### Post by RichPicker on 2007-04-07
I agree. The error was not my installing the updates; the error was within the update itself, placed there by a developer.

The new update for the mic arrived. I tried Method A and B, but still the mic does not work. Method C is beyond my ability and understanding (and the instructions are vague). Is anyone willing to help me with this update - to get my mic working  again?

PS: It's the developers who  are in need of a magic bullet, not the generic users.

---

### Post by carusoswi on 2007-04-08
I just lost my sound, sort of.  My Realtek AC97 is no longer in my list of audio cards, just some dsp1.  I don't understand it, but would like to know how to restore the correct driver (if it is, indeed, uninstalled for some reason). I'm not interested in turning off downloading or whatever broke this item, more interested in learning how to fix it when I break it again.

Any suggestions would be welcome.

Caruso

---

### Post by carusoswi on 2007-04-08
Ok, it seems that I did not lose my sound.  I have two sound cards, the Realtek 97 which is an onboard card, and my Audigy 2 that is in the PCI slot.  Seems that I somehow managed to configure Ubuntu to not recognize the onboard card when it boots or makes other system sounds.  Only the PCI card does that now.  

When I run audio aps, I can switch between the two cards (they are labeled DSP and DSP1 - is that correct?).

Still struggling to get my head around this Ubuntu Linux stuff.  It's a struggle sometimes.

Caruso

---

### Post by RichPicker on 2007-04-11
Three suggestions recently came out to fix the microphone problem. None of them work on my laptop, and reinstalling the sound modules seems to have created more problems, and I was once again scolded for complaining.

---

