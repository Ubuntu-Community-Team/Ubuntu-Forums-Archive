---
title: "sound probs switching from ubuntu - kubuntu"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Simran on 2007-06-22
I thought i would give kubuntu a try, so i went ahead and installed it. all seems to be working fine other than my sound.

card = 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

The sound icon in the toolbar says its muted and when i adjust it to change the volume nothing happens just says Volume: 40% but its still muted.

worked fine in ubuntu after doing this 

Add "options snd-hda-intel model=3stack" at the end of /etc/modprobe.d/alsa-base

any ideas, can give more info if needed :)

Simran

---

### Post by abn91c on 2007-06-22
in kmixer check the PCM setting

---

### Post by Simran on 2007-06-22
PCM is set to 100% :S

---

### Post by abn91c on 2007-06-22
make sure all the radio buttons are green, also in a terminal type alsamixer to check if kubuntu id's your sound card, play with the settings ther, make sure nothign is muted

---

### Post by Simran on 2007-06-22
Ok i ticked the green thing and now it doesn't say muted any more, but i still get no sound the alsamixer picks up my sound card though.

---

### Post by Simran on 2007-06-22
actually it turns out after maxing everything out, the sound is so quiet you can only just hear it with headset on. so i need a way of amplifiying this :S

Sim

---

### Post by abn91c on 2007-06-22
i don't mean to state the obvious but check the speaker volume knob or where it plugs in on the sound card in case it became dislodged or loose

---

### Post by Simran on 2007-06-22
its a laptop, so integrated speakers. i guess i should have stated that before. Its just odd that it works perfect on ubuntu, but kubuntu its a pain if i could get this working i would give kde a shot for longer than about 20 mins

sim

---

### Post by abn91c on 2007-06-22
if everything is on green and the laptop dont have a volume knob, (some do by the way you may have to check the FN key combinations) go to the kde website and search the forums and wiki's there

---

### Post by Simran on 2007-06-22
ok thanks anyways :)

---

