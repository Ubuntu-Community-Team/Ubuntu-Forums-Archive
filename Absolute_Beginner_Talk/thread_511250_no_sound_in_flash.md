---
title: "no sound in flash"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by natman on 2007-07-27
I have firefox 32 running on my 64 bit machine and flash works, but i do not get any sound. I was having a lot of problems just getting sound to work on the machine in the first place. Anyone know a way i can get it running - i would prefer not to mess with my ALSA settings so i do not upset the rest of the sound.
Any ideas?

---

### Post by st33med on 2007-07-27
64 bit? There is currently no flash that supports 64 bit. That might be the reason you're having trouble.

---

### Post by natman on 2007-07-30
Like i said i am running 32 bit firefox ( with flas ) in 64 bit kubuntu, there must be a way to get the sound working?? without srewing with my alsa driver setting??

---

### Post by deadgobby on 2007-07-30
[https://help.ubuntu.com/community/FirefoxAMD64FlashJava](https://help.ubuntu.com/community/FirefoxAMD64FlashJava)
 If you have a on board sound card and a PCI card like sound blaster. You need to disable the on board card in your BIOS. This will have all sound to default to your sound card.
Gobby

---

### Post by natman on 2007-07-30
Im not really sure that i want to try that since i had soo much trouble getting my sound card found in the first place, i really dont want to screw around with default sound cards, is there not some setting that i can change that tells firefox how to output sound?

---

### Post by asmoore82 on 2007-07-30
the last time i checked (its been a while),
the proprietary flash plugins could only use OSS for sound and not ALSA

so, first thing is to get the 'alsa-oss' package if you don't already have it.
And, the other little quirk of OSS is that if any sound is already playing when
the flash video starts, the sound will not work until you close and open firefox again.

---

### Post by natman on 2007-07-30
after checking turns out i already have alsa -oss installed

---

### Post by RaisunH on 2007-07-30
I just got Ubuntu and couldnt get the sound to work with my Soundblaster Audigy SE at all, even though the system seemed to detect it ok. But luckily I have an on-board sis sound chipset...

It really is a straight forward thing to boot into the bios (just hit Del when booting) then enable or disable the chipset. 

Now I have music in my ears while i write this :)

I'd prefer a sis sound device and sound, than the Audigy and nothing ...

---

### Post by natman on 2007-07-30
Thanks for advice, im after trying but unfortunatly no luck with flash sound, anyone else have any other ideas?

---

### Post by asmoore82 on 2007-07-31
Open "System -> Preferences -> Sounds"
-OR-
```
~ $ gnome-sound-properties
```
and click "Sounds" Tab

the very first checkbox should be "Enable software sound mixing"
somtimes the software mixing daemon can be greedy with the sound device
even when no applications are playing sounds. This causes a confusing
"Device already in use" error in OSS applictations.

So, turn off "enable software sound mixing"
-AND- Very Important
```
~ $ killalll esd
```

Then close and open Firefox and give it one last shot!

---

### Post by natman on 2007-07-31
Thanks but unfortunatly, no joy, the "enable software mising box had not been selected" i checked it and unchecked it and killall and variou combinations still no sound in flash!

---

