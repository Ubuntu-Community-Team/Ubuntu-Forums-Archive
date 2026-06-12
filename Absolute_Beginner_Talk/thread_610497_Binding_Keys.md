---
title: "Binding Keys"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-12
**This post could be related to an Ubuntu bug filed at**:   [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hey there, i'm on a laptop, originally it came with windows vista, but i switched to ubuntu. On it there is a "media station" i guess you could call it.  It's just a few buttons like "pause" "play" "stop", etc.  Is it possible to bind one of these buttons to load rythymbox? thanks

---

### Post by akadruid on 2007-11-12
Go to System>Preferences>Keyboard shortcuts, then scroll down until you see the sound section. click on setting you want (e.g 'Play') then press the button you want to correspond to it.  It should enter some weird code for you, and you're all set.

On my Dell M1210 laptop, these were set by default when I installed Ubuntu into a virtual machine, but can be changed by the above method.  The 'play' key for example shows as '0xa2' on mine, and 'Skip to next track' shows as 0x99.  These should all work with rythembox by default.

If you are just interested in launching rythembox, the 'Launch music player' one should do that I think, but I have not tried it.

---

### Post by jordank on 2007-11-12
i dont have a "launch music player" option.  Can i define one?

---

### Post by jordank on 2007-11-12
Like, play and everything works while i'm in rythym box, it's just i want something to launch it.  I have a "pwr" button, that in windows would normally launch the media centre.  It does nothing by default now, in linux.  I want to set it to launch rhythym box, but can't figure out how to do that.

---

### Post by akadruid on 2007-11-12
Hi, I just got home and on my home desktop it is labelled 'Media player' instead, still in the sound section.  I just bound my right windows key (shows as Super R) to 'Media player' and it launched rhythmbox.  Does that work for you?

---

### Post by jordank on 2007-11-12
Yeah, i can bind media player to super R, which works and opens up rhythym box correctly, however, when i try to bind it to a button that isn't part of the Keyboard, per se, but more part of the laptop, it doesnt recognize it.  How can i bind this button to actions?

---

### Post by akadruid on 2007-11-13
It could be that the key is not recognized by Ubuntu for some reason.  What is the make and model of your laptop?

I've been playing with my laptop again, looks like I have a similar thing with one of the keys.  Mine is a Dell M1210 and it has a button next to the power button that does the quick launch thing when the machine is off, and that does nothing in the key binding dialog.

I think this means it's going to get more difficult from here.  Unless googling for your laptop name, linux/ubuntu, and 'pwr button' or 'media button' turns up anything then we might have to do it the hard way.  There is a complicated but pretty complete set of instructions for this here: [http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys](http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys)

When I get a minute I will try and figure out how to do this for my dell.

---

### Post by jordank on 2007-11-13
I've got the Asus gaming series G1.
[http://event.asus.com/2006/nb/g1g2/supreme.html](http://event.asus.com/2006/nb/g1g2/supreme.html)
Not a very good website for stats, but you can at least see it :S

---

