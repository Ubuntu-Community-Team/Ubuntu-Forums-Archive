---
title: "USB sound card, part working"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Spaced Monkey on 2007-03-13
Hi,

I've got Dapper running on a laptop, generally quite happily.   But, a while ago I managed to break the headphone jack, so I bought a USB sound interface.

I went to preferences, and something in administration and got audio working in Amarok, XMMS, Firefox and the general desktop (ie, it makes noise through my headphones at startup, the headphones are plugged into the USB sound adapter).

But, I cannot get sound in any video apps, Totem, GXine, Mplayer, VLC all play the picture, but without sound.   This is quite irksome :/   I went into VLCs preferences and told it to use the USB audio (I chose also too I think) but nothing changed.   (Chose to play with VLC as I'm familiar with it from XP).   Had a poke around the other players but couldn't get them to work either.

As far as I can tell, the USB one is now the default audio device in all other respects.

Looked in the multimedia forum btw, but all similar posts seem to have no replies.

Help, please?

SpacedMonkey

---

### Post by bernied on 2007-03-13
This is just a guess, but another way to try to fix this might be to reinstall the affected packages - maybe sound is configured as part of the installation. So maybe:
```
sudo apt-get remove mplayer
sudo apt-get install mplayer
```

Some packages might also support dpkg-reconfigure, like
```
sudo dpkg-reconfigure mplayer
```

The second option is probably faster and less destructive (I don't know what will happen to all your configured options, so be careful.

Don't get carried away with this, if it doesn't work for one or two, it probably isn't a good idea at all.

---

### Post by bernied on 2007-03-13
The other thing that occurs to me is to blacklist the module for your on-board sound - I can't remember how to do this but google will remember.

And how broken is that jack? Is there a bit of plug stuck in it? Have you tried the superglue on the end of something-long-and-thin trick?

---

### Post by Spaced Monkey on 2007-03-13
Hi Bernied,

 I tried a reinstall of mplayer via the method you suggested, and I did a reinstall of totem through synaptics, but sadly nothing changed.   

I have noticed though, that in system-<prefs->sound the default sound card is always "intel... whateveritwas" rather than the USB one, even after manually changing it.   It just keeps reverting.   I'm not sure if there's a clue in that.

The jack is pretty much borked, I tripped over my headphone lead one day sending the laptop flying, and the side pressure did something.   If I plug headphones in all the way, I get occasional sound in one channel, and if I type, the motion seems to jitter the connection and sound cuts in and out.   So, not much hope of salvage I fear.

I'll have a google for the blacklisting approach, thanks for suggesting it.

S-M

---

### Post by Spaced Monkey on 2007-03-13
Bernied,

Next time I'm in Edinburgh you are officially entitled to a pint :)
Blacklisting it did the job.

For future searchers, here's what I added to /etc/modprobe.d/blacklist
(although as always, YMMV).

[I]#blacklist internal soundcard so USB one overrides
blacklist snd_intel8x0
blacklist snd_ac97_codec
blacklist snd_ac97_bus[/I]

SpacedMonkey
(now with sound!)

---

### Post by bernied on 2007-03-13
> **Spaced Monkey said:**
> Next time I'm in Edinburgh you are officially entitled to a pint :)You've made me thirsty.

---

