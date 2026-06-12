---
title: "Install Sound Card : Sound Blaster Audigy 2"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by blackrabbit on 2007-06-05
I'm pretty new to Ubuntu, and my sound drivers dont seem to be working right. I've tired a bunch of things with alsa, but no luck. I have a Sound Blaster Audigy 2. I was wondering if you guys could be of any help. Thanks

---

### Post by kevdog on 2007-06-05
Id be curious in this answer myself!!!

---

### Post by iceportal on 2007-06-06
My sound card worked perfectly last night, but I turn my computer on today and it doesn't work? I'm using a Creative Labs Sound Blaster Audigy 2 card...

Help!

---

### Post by metaverse on 2007-06-06
I'm in no place to offer advice but after trying to diagnose my audigy 1 problem - I'll toss this goofy fix that probably won't help you.  I wasn't getting any sound, but it was clear that my audigy was being seen, etc.

Going into volume control -> switches -> and then de-selecting the Analog/Digital checkbox (since I'm just using headphones).

---

### Post by iceportal on 2007-06-08
Turns out all I had to do was reboot. :-P

---

### Post by JerMe on 2007-06-19
> **metaverse said:**
> I'm in no place to offer advice but after trying to diagnose my audigy 1 problem - I'll toss this goofy fix that probably won't help you.  I wasn't getting any sound, but it was clear that my audigy was being seen, etc.

Going into volume control -> switches -> and then de-selecting the Analog/Digital checkbox (since I'm just using headphones).

Worked for me, thanks.  Hopefully this information will be helpful for the next person searching for the forums for a sound issue.

---

### Post by iceportal on 2007-06-19
So... Just wondering... But has anyone else experienced troubles with their sound card where it works fine one moment, but on reboot it stops working, only to start working again after another reboot or two?

(Somewhat Unrelated: The login screen text size also changes from normal to tiny-unreadable sometimes when I reboot. Odd.)

---

### Post by seancca on 2007-06-25
I have noticed this as well, does your MoBo have build in sound? It seems to want to switch but wont output sound if you switch in in the sound panel. I wonder why it does this. Even if it is set to be on that and when i restart it still has that listed as the sound card but it plays out of the other one.

---

### Post by iceportal on 2007-06-25
I've got the SB Audigy2, and it's the only sound card I'm using... I'm sure there's a built-in sound card on the motherboard like you suggested but I'm not using it.

You think it's switching between the two? I'm not even changing anything...

I could start it now and sound will work, and then without touching anything I could restart and next time sound wouldn't work. And vice versa.

Odd.

---

### Post by aquilla on 2007-07-06
> **iceportal said:**
> I've got the SB Audigy2, and it's the only sound card I'm using... I'm sure there's a built-in sound card on the motherboard like you suggested but I'm not using it.

You think it's switching between the two? I'm not even changing anything...

I could start it now and sound will work, and then without touching anything I could restart and next time sound wouldn't work. And vice versa.

Odd.

I have the exact problem, please help or pm when you find any solution.

---

### Post by CautionaryX on 2007-07-06
You'll probably have to boot into the BIOS and physically change the setting for onboard sound to disable it. That way the only audio controller should be the SB Audigy.

---

### Post by flipptastic on 2007-07-08
CautionaryX, thank you man, I can't believe that it was that simple, for the past week or so I was trying all sorts of things to get the sound working and this was all I needed to do. I'm pretty sure a majority of people whose pc's are outfitted with a standalone sound card and onboard sound are having problems because they did not disable the onboard sound manually from their bios. Btw, I also had an audigy 2, and everything works very well now. :biggrin:

---

