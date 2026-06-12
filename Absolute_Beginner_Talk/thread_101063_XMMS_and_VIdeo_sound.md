---
title: "XMMS and VIdeo sound????"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by adduds on 2005-12-09
How come when XMMS is playing a song i can't watch a video i.e. on video google and hear it's sound?

---

### Post by Qrk on 2005-12-09
Linux doesn't handle multiple applications using the sound card at once very well. XMMS is fairly old, some of the newer stuff that may work better isn't in it. Actually, I think the reason Windows XP (correct me on this someone, if I am wrong) does do well with sound is because XP takes control over access to the sound card; then delegates it to applications.

---

### Post by adduds on 2005-12-09
Ya but their's a driver I can d/l, because the last time i was fixing my sound (the first time i had ubuntu on) i d/led a shit load of sound drivers and ish, that ppl told me 2 and i guess one was for the dual sound....

anyone know which one it is?

i have an Intel ICH4 soundcard

---

### Post by adduds on 2005-12-09
anyone know the driver???

---

### Post by Kimm on 2005-12-09
If you want multiple sounds consider using ESD (polypaudio was good in Hoary but I got better results with ESD in Breezy), most apps support it and and it does pretty much the same as the windows sound.

> 
XP takes control over access to the sound card; then delegates it to applications


ESD does pretty much the same thing

---

### Post by adduds on 2005-12-11
is their  a way to have it w/ the ALSA drivers?

---

### Post by malli kalu on 2005-12-11
[QUOTE=adduds]How come when XMMS is playing a song i can't watch a video i.e. on video google and hear it's sound?[/QUOTE]
[mk]I'm sorry, i hava not ans for that problum.but i hava a same problum, i can't play mp3 or mpeg in my computer. i'm useing ubunthu 5.10. can you help me

---

### Post by adduds on 2005-12-15
> [mk]I'm sorry, i hava not ans for that problum.but i hava a same problum, i can't play mp3 or mpeg in my computer. i'm useing ubunthu 5.10. can you help me

did you fix it yet?

---

### Post by BoyOfDestiny on 2005-12-16
[QUOTE=adduds]is their  a way to have it w/ the ALSA drivers?[/QUOTE]

Yes! I have an audigy2 platinum, not a zs (hope this still works for you). With alsa I can have many apps at once (tested with like 6) and produced a wonderful cacophony...

I should just make this a how-to... maybe I will after I type it out here:

Using synaptic,
install alsa-oss and libsdl1.2debian-all

Next step (this one may be optional, I just hate the gnome sounds and ESD)

Go To System -> Preferences -> Sound
uncheck Enable Sound Server at start up and gnome system sounds

Next step
Go To System -> Preferences -> Multimedia Systems Selector

Set the default sink input and output to ALSA

If you did choose to not have esd, open up a terminal and type sudo killall esd. Or if you are more gui oriented log in and out of ubuntu.

Now, if you are lucky, open up xmms, beep, zsnes, dosbox, audio overload, etc etc. You should hear multiple sounds like nobody's business. Remember, if any of these apps were manually set to use ESD as default ouput, use their respective guis to set it to alsa or oss (if alsa isn't an option).

---

