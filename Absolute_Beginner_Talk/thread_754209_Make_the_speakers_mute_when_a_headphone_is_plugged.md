---
title: "Make the speakers mute when a headphone is plugged in"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by koba101 on 2008-04-13
Hi,

Is there a way I could configure Gutsy to make the sounds on the speakers disappear when a headphone is plugged in to the frontpanel? (or back)...i've got this on widows 

My sound card is built-int (Intel mobo classic series)

---

### Post by Duckyspetrie on 2008-04-13
Basically, you're are wanting to mute the computer when you plug heaphones in?

---

### Post by koba101 on 2008-04-13
yes...i still want to hear the sound through the headphone though

---

### Post by udh on 2008-04-13
yeah, i know this problem. 
When you plug in headphone in, the volume from the external speakers stops, which is ideally correct.
But in ubuntu, I too experienced this same problem that when I plugged in microphone, my external speakers kept on playing music. I could hear both thru headphones and ext. speakers. 
It was strange.
I downloaded updates as usual and it somehow solved the problem. 

You need to update alsa-sound drivers, just search for that on this forum, should solve the problem.:guitar:

---

### Post by koba101 on 2008-04-14
interesting...you got gutsy right?

---

### Post by udh on 2008-04-14
yeah, gutsy gibbon 7.10:guitar::popcorn:

---

### Post by Mick8882003 on 2008-04-14
are the headphones on the same socket?

like one at the front and one at the back?

if they run off the same output you might have to unplug the speakers, take the speaker output from the front to be helpful

---

### Post by Trail on 2008-04-14
You probably need a newer version of ALSA (Advanced Linux Sound Architecture) for this to work correctly. The version on the repositories is .15 i think, but the latest release is .16 (which works for me).

If you can't/don't want to compile it yourself (which is quite a work to do, could take an evening for a mid-newbie), you could try waiting for 8.04, which should have the newest version of ALSA.

Optional:
try pasting this in a terminal:
```

sudo lshw -short | grep Audio

```

If it returns a line like "/0/100/1b                        multimedia  82801H (ICH8 Family) HD Audio Controller", then you have the same audio card as me, and it is probably the alsa version that I'm mentioning.

---

### Post by koba101 on 2008-04-14
nice...you made me type the code in your signature as well....I do have the same sound card as you....if you can tell me where i can find .16 installation instructions...that would be great

---

### Post by stchman on 2008-04-14
> **koba101 said:**
> Hi,

Is there a way I could configure Gutsy to make the sounds on the speakers disappear when a headphone is plugged in to the frontpanel? (or back)...i've got this on widows 

My sound card is built-int (Intel mobo classic series)

My Toshiba has a Intel based HDA sound card and installing ALSA 1.0.16 did the trick for me.  I have a script and tutorial to do this.

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

I then used the tips to then mute the speakers when the headphones plugged in (middle tip).

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

Hope this helps.

---

### Post by koba101 on 2008-04-15
it killed all the sound i had...how do i revert

---

### Post by koba101 on 2008-04-17
anybody....still need some help here

---

### Post by koba101 on 2008-04-21
anybody?

what happened to all the geniuses?

---

