---
title: "Drivers!!!"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by nikoPSK on 2007-09-20
hello everyone. I have a few things on my pc which I have still not found drivers for:

My winfast TV2000 XP series (Xp suggests mabye it doesn't work with linux):(
And my Sound blaster audigy. I've had to re-enable onboard audio which is terrible... mabye I was just spoiled with my high end stuff. I'll also need something to watch the tv on. howabout an alternative to myth tv..:)

---

### Post by dresman on 2007-09-20
that really new stuff doesnt work good appcept for windows and windows sucks:)Either stick with windows or give it back to the place you brought it from.whhatever you have sounds pretty wierd:confused:

---

### Post by qamelian on 2007-09-20
> **nikoPSK said:**
> hello everyone. I have a few things on my pc which I have still not found drivers for:

My winfast TV2000 XP series (Xp suggests mabye it doesn't work with linux):(
And my Sound blaster audigy. I've had to re-enable onboard audio which is terrible... mabye I was just spoiled with my high end stuff. I'll also need something to watch the tv on. howabout an alternative to myth tv..:)

You shouldn't be having any trouble with the Audigy. The drivers are already built in. My Audigy 2 works beautifully out of the box. Can you give some detail regarding what was not working with the Audigy card?

---

### Post by nikoPSK on 2007-09-20
When I plug in my speakers... No sound!!! And I can't really return the pvr card because I'm not the one who bought it. My uncle got it for me a while ago heaven knows where and has probably lost/ disposed of the receipt :(

---

### Post by qamelian on 2007-09-20
> **nikoPSK said:**
> When I plug in my speakers... No sound!!! And I can't really return the pvr card because I'm not the one who bought it. My uncle got it for me a while ago heaven knows where and has probably lost/ disposed of the receipt :(

Go to Applications > Acessories > Terminal and type ```
alsamixer
```
Make sure the right sound card is selected and check the levels of each channel. It's possible that some levels are zero'd or muted. It is also possible that alsa was trying to use the wrong card.

---

### Post by Maestro23 on 2007-09-20
> **qamelian said:**
> Go to Applications > Acessories > Terminal and type ```
alsamixer
```
Make sure the right sound card is selected and check the levels of each channel. It's possible that some levels are zero'd or muted. It is also possible that alsa was trying to use the wrong card.

Beat me to it.  Always good to check the "usual" suspects. :smile:

---

### Post by nikoPSK on 2007-09-20
Unfortunately for me, I do not know what to do or what half of it means...:lolflag:

---

### Post by Maestro23 on 2007-09-20
> **nikoPSK said:**
> Unfortunately for me, I do not know what to do or what half of it means...:lolflag:

When you run the command alsamixer, you should see a screen that kinda looks like an EQ.

Arrow keys are to move.

"M" toggles Mute ON/OFF.

All you got to do is make sure the proper channels are not muted and the volume is turned up.

It's pretty self-explanatory.

---

### Post by nikoPSK on 2007-09-20
Thanks.:KS

---

### Post by nikoPSK on 2007-09-25
K so now I got 7.10. My printer won't work!! (HP Deskjet 932C) It recognizes it and queues the printer but nothing comes out.... Still havn't fixed the audigy problem...:confused:

---

### Post by grege on 2007-10-24
On some motherboards even though you turn off the onboard sound in the BIOS linux still finds the chip and makes it sound card zero and the Audigy sound card one.

open a terminal and type su gedit /etc/modprobe.d/alsa-base

at the end of the file add a line

options snd-emu10k1 index=0

yours might be snd-emu10k2, just have a look through the file and identify the card.

then restart and in future the system will force the card to be the main one and all should work.

good luck

:)

---

### Post by jkeyes0 on 2007-10-24
I have an audigy, and upgraded my system to gutsy last night, and I was given an error message that said I needed to select my default sound card. I did this in the following way:

1.) Click Applications -> Accessories -> Terminal
2.) In the terminal, type "asoundconf list" and hit enter. This should show your list of installed sound cards.
3.) To select a card, type "asoundconf set-default-card XXX" where XXX is the name of the card (most likely Audigy, as that's what mine was).

Hope this helps.

---

### Post by nikoPSK on 2007-10-24
ok, when I get home I'll give that a try.:)

---

### Post by tim heeter on 2007-10-24
If you don't know the model of the sound blaster your using that might be a problem though. Are you using any soundblaster from the X-FI family?

---

### Post by nikoPSK on 2007-10-24
> **tim heeter said:**
> If you don't know the model of the sound blaster your using that might be a problem though. Are you using any soundblaster from the X-FI family?

I have no idea... The driver disks for windows that came with it just say audigy on the front...

---

### Post by nikoPSK on 2007-10-24
k

It worked. Audigy was listed so I did that, but does the sound start right away? Or do I re-boot? Because I don't hear anything when I plugged it in to my audigy...

---

### Post by nikoPSK on 2007-10-24
nvm, just had to unmute a channel and mute another in alsamixer:KS Thanks for everything

---

