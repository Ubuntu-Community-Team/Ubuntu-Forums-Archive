---
title: "I have no sound"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by roostercogburn on 2005-11-29
i can play cds and mp3s but there is no sound i can see them playing on xmms

---

### Post by detyabozhye on 2005-11-30
Can you give us more info, like what sound card you're using?

---

### Post by goodmanbrown on 2005-11-30
More details would certainly be helpful.

It sounds, though, like at some point in the chain your volume is just turned down or muted.  Try double-clicking on the volume applet on your top panel, and make sure that both "Master" and "PCM" are turned up at least part of the way.  You can also run alsamixer from the command line to accomplish the same thing.

---

### Post by adduds on 2005-11-30
Well i can give you details about mine...i'm running a Gateway 3550z laptop, it has **Intel 82801DB-ICH4** sound card. i downloaded the latest **alsa-driver-1.0.10 drivers** i see the sound levels are all (in terminal alsamixer) up; UNMUTED LOL, 

i can play cd's i **see **it playing, but have no sound. i tested between alsa, oss, Artsd, ESD in System-->Prefs-->Multimedia Systems selector

I can even play dvds i have the dvdcss2 and **win32 codes**, but i have no sound...n00b here, any ideas?

i **really **like ubuntu Breezy, i just need some help THANKS! SO WE'RE IN THE SAME BOAT BUDDY! 

thanks/cheers,
ad

ps. **didn't mean** to hoarn into you thread it's just i have the same problem :)

---

### Post by adduds on 2005-11-30
Anyone??? ^^^^^^^^^

---

### Post by Rumor on 2005-11-30
[QUOTE=adduds]
i can play cd's i **see **it playing, but have no sound. i tested between alsa, oss, Artsd, ESD in System-->Prefs-->Multimedia Systems selector

I can even play dvds i have the dvdcss2 and **win32 codes**, but i have no sound...n00b here, any ideas?

i **really **like ubuntu Breezy, i just need some help THANKS! SO WE'RE IN THE SAME BOAT BUDDY! 
[/QUOTE]

What worked for me was going to system | prefs | sound and choosing my sound card as the default sound device. Until I did that, I had no sound either.

Might not help you, though. :confused:

---

### Post by adduds on 2005-11-30
> If at first you don't succeed, skydiving is not for you.

That's an amazing tag hahahah!

---

### Post by adduds on 2005-11-30
My soundcard is chosen as my default....

thx though!

Anyone else have any ideas?

ANY HELP WOULD BE GREATLY APPRECIATED

---

### Post by detyabozhye on 2005-11-30
I don't know much about your particular sound card, so I can't help with it, sorry.

---

### Post by patrick295767 on 2005-11-30
maybe : chmod 666 /dev/dsp
  
or 
  
alsamixer 
(up down and m key)
  
Good  beginning with linux !!
  
Pat'

---

### Post by roostercogburn on 2005-12-01
Hey I still cant figure out the problem I have a Radeon RV100 QY [Radeon 7000/VE] sound card. Any more ideas. :confused: 

Thanks.

---

### Post by solarcontrol on 2005-12-01
oops.
trying alsamixer was already recommended..

since you have a sound card, there is a good chance you also have an onboard sound chipset.
alsa is probably using it.
try plugging your spkrs into the onboard sound jack to confirm this.
if the case, 
try opening a terminal and typing alsaconf (or alsaconfig - cant remember) then go thru the config steps and choose your new card.

then reboot.
at that point it should work.

---

### Post by adduds on 2005-12-01
I think it has something to do w/ my speakers and not even my soundcard anymore, because i re-installed microsoft XP b4 i installed ubuntu like a week ago, and they didn't work then... :confused: :confused:...but i have alsamixer in term. and nothigns muted and everythings maxed so theoretically it should work right....?

---

### Post by solarcontrol on 2005-12-01
try some headphones?
they will at least tell you which jacks are putting out sound.

the fact that the player is "playing" tells me that its probably not a driver or hardware problem. its more likely the spkrs or simply the OS using the onboard sound rather than the card.

---

### Post by BobSongs on 2005-12-02
hehehe

Thought I'd throw in my problem as well.

**System:**
Generic slap-together
Pentium III 933 MHz
512 Mb RAM
SoundBlaster Live!

Problem:
XMMS plays CDs but produces no sound. All other applications produce sound. The CD Player plays CDs normally. But XMMS makes no sound at all. If I shut it down and play CDs through other applications, all is well.

I imagine the simplest solution is to stop complaining about it and use something else. But I'd like to play .mp3 of my CDs too. It's almost like there's some initial setting that isn't set right. All system sounds work fine. Just XMMS.

Feel free to ask for more info. Glad to offer it.

Thanks!

---

### Post by BobSongs on 2005-12-03
Well. I tried something radical. I re-installed Ubuntu from scratch.

XMMS works now.

:rolleyes:

---

