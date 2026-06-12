---
title: "Audio hardware, AC97"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by Taigrr on 2006-10-07
Okay, i've almost got this thing working! I fought the mad battle over wireless Broadcom, with triumphant results. 

I found how to get my Radeom drivers to work oh so right, while later finding that I couldn't have both the Broadcom wireless and the ATI Radeon at the same time. A battle for another day.

Now, sound is in my midsts. MY card comes up as an ATI ixp (Or something like that), but emachines says it's just a generic AC '97, and any driver should work. I'm finding that's not hte case. In Windows, under sound, all the drivers that come up in Device Manager are 

"Audio Codec, Conexant AC-Link audio, Legacy Audio drivers, Media Control Devices", for ones maybe related to Sound.

But, in Ubuntu, it doesn't work. "Volume Control" connects to something, but I think it's finding that ATI Driver, which apearently doesn't work.

OFf a fresh install, I tried "sudo apt-get install Alsa*" and "sudo apt-get install GStreamer*", wondering if it'd have any affect, but it didn't.

Does anyone have any hints?

---

### Post by CatKiller on 2006-10-07
I don't know if it will have exactly the right solution for you, but [the Comprehensive Sound Problem Solutions Guide]("http://www.ubuntuforums.org/showthread.php?t=205449") might at least point you in the right direction.

---

### Post by Taigrr on 2006-10-08
When I type "aplay -l", it shows "ATI IXP AC97". One of them is "Card:0 IXP [ATI IXP]", and the other is card 1: Moden [ATI IXP Modem]".

Is the Card 0 sound, or is aplay -l not picking up my card?


Edit: Also, if that is my card, it says "Subdevices: 0/1", which would lead me to beleive something's missing, which is why I can't get sound. 

So first of all, Is that the sound card it's picking up? And Second, is that Subdevice what's screwing with me, and do you know where to find whatever I need to fix it?

---

### Post by CatKiller on 2006-10-08
> **Taigrr said:**
> When I type "aplay -l", it shows "ATI IXP AC97". One of them is "Card:0 IXP [ATI IXP]", and the other is card 1: Moden [ATI IXP Modem]".

Is the Card 0 sound, or is aplay -l not picking up my card?

Seems likely that Card 0 is your card. And A WinModem isn't a modem at all - it's a card that makes beeps. Hence why it gets picked up as a sound device, and why you automagically get a modem with your onboard sound.

> Edit: Also, if that is my card, it says "Subdevices: 0/1", which would lead me to beleive something's missing, which is why I can't get sound. 

No, that probably means Subdevices: **0** & **1**, not Subdevices 0 "out of" 1.

> So first of all, Is that the sound card it's picking up? And Second, is that Subdevice what's screwing with me, and do you know where to find whatever I need to fix it?

[Technically, here]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=ATI&card=ATI-IXP+southbridge+AC97+audio.&chip=IXP+SB150%2C+IXP+SB200%2C+IXP+SB250%2C+IXP+SB300%2C+IXP+SB400&module=atiixp"). And the Comprehensive thread. I don't know enough about Linux sound to get your particular module working with your particular computer.

---

### Post by Taigrr on 2006-10-08
Well, thankyou for the help, but I think this laptop is going back.

It just plain doesn't work. It works better out-of-the-box with Ubuntu than it does with Windows XP, which it was designed for.

So, thankyou all for the help. I learned alot! But, I give in.

---

### Post by CatKiller on 2006-10-09
I think that Lenovo might make laptops that come with Linux, so the hardware should work. Or you could check the Hardware Compatibility wiki page to see which laptops others have got to work.

---

