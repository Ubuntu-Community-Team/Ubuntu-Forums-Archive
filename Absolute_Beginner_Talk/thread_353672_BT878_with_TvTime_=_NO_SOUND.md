---
title: "BT878 with TvTime = NO SOUND"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Contrid on 2007-02-05
Hi there,

I've been searching and searching, but I can't find anything to solve my problem. I've also tried changing settings wherever I can, but it also doesn't solve my problem.

I have a Conexant BT878 tv card which I'm currently using through TvTime. There is picture (channels), but no sound.

I have an internal sound card with speakers and then I also have a Logitech USB headset. Neither of them work. Sound on these devices work with audio cd's, system sounds, etc...

Please help me to get my sound on television through tvtime.

Thanks alot for your help.

---

### Post by Contrid on 2007-02-05
Any ideas?
I've tried several things since, but I still can't get sound.
Any help would be greatly appreciated.

---

### Post by fenian on 2007-02-05
Sometimes you have to take the audio out from the tuner card and patch it into the soundcard.

---

### Post by camini on 2007-02-05
Same here, Hauppauge BT878 card on /dev/video1 gives picture but no sound in tvtime.
The output from the tuner card indeed goes to the soundcard with a cable connection - works fine under windows xp, but not in tvtime.
Sound in Ubuntu works fine otherwise.

---

### Post by Contrid on 2007-02-05
I have a cable coming from my "audio out" on the tv card to the "line in" on the soundcard.

I hear a monotone scratching sound like you hear when there's no signal, but when I turn the speakers up to full volume, I can hear the sound very very softly behind the loud scratching sound.

Maybe my sound card isn't installed correctly !?
Although...I do have sound with everything else.

---

### Post by Contrid on 2007-02-05
Tell me...what command do I use to see the location of my devices? Like "/dev/video1" but just for the sound devices. I want to know what my USB headset is on.

---

### Post by chalex on 2007-02-05
For my tv tuner, the sound comes out of the audio output of the tv tuner card.  Can you at least test with headphones that sound is coming from there?  Then you can work on patching the sound through the line-in of your sound card.

---

### Post by Contrid on 2007-02-05
> **chalex said:**
> For my tv tuner, the sound comes out of the audio output of the tv tuner card.  Can you at least test with headphones that sound is coming from there?  Then you can work on patching the sound through the line-in of your sound card.

Thanks, good advice.
When I plug my speakers directly into the "audio out" of the tv card, I don't hear anything. Maybe the tv card isn't installed/configured correctly.
Where would be the best place to start checking?
Any help would be greatly appreciated.

---

### Post by Contrid on 2007-02-05
Ok...it's working!!!
I honestly don't know what I did. I just rebooted and it worked. :D

Now...how can I get the sound to come through my USB headset instead of my speakers? If someone could help me with this, I will be very greatful.

---

### Post by hitekhal on 2007-02-05
if using gnome, which is default, be sure you have
gnome alsa mixer
installed

then open mixer and unmute your input

for the life of me i don't know why the default for the mixer is always mute

seems to be the norm for all linux flavors and alsa

---

