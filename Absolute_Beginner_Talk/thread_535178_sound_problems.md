---
title: "sound problems"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by asathorny on 2007-08-26
Well, when I say sound problems what I mean is no sound at all.  I am a real newbie who installed Ubuntu 24hrs ago.   I am suitably impressed with its ease of use having tried other flavours of linux over the years.  This was really easy to install once it dawned on me that the disk loading version was to heavy and got the txt version.

The details are as follows:-
Satellite Pro 4600
Ubuntu 7.04... wikth all the post install updates.
and a wired connection to my router (which works fine straight out of the box)

I am not at all sure what my sound card is, but it is the standard card for the laptop.

I have searched without success from one source I tried using the terminal mode and typed 'apaly -1' which failed to solve the problem and also '1spci -v' which also did not help me.

Any help would be appreciated and I thank you in advance.

asathorny

---

### Post by K.Mandla on 2007-08-26
Here's a couple more commands that might help.

```
amixer scontrols
```
That should give you a list of controls available to your sound card. According to this

[http://www.tuxmobil.org/toshiba_sp4600.html](http://www.tuxmobil.org/toshiba_sp4600.html)

It should work in some form or another. Try *lspci -vvv* again (it's an "L" not a "1"), and see if you get similar information to what's on that page.

Also,

```
lsmod | grep snd
```
should tell you what sound modules have been inserted. There's always the possibility that the sound modules aren't the right ones for your card.

Aside from that ... is the volume turned up? :mrgreen: Try this 

```
alsamixer
```
and see if there's anything there that you can adjust and get sound. Remember that some channels might be muted, so unmute the ones that you can.

---

### Post by asathorny on 2007-08-26
Thanks for the input K.Madla...

I'll give these a try out and see how that goes.  In the meantime I am more than impressed.

Thanks again

---

### Post by asathorny on 2007-08-26
OK I did the things suggested and it all looked really promising, the sreen flung open and filled with lots of information as follows:- 

snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm

I have to confess that this told me nothing since I only speak a couple of Earth languages and this seems to be in neither of these.  I am certain that someone here will know from this why I am sat here in slience and if you could pass that knowledge along to me  I woujld be neverendingly grateful.

The AC 97 thing seemed to ring distant bells in my aging brain but I can't think why.

Thanks in adance once more....
a real dumd beginner

---

### Post by asathorny on 2007-08-27
It's time to come clean....

Sound problems solved, the problem was my stupidity, not Ubunto.

I thought I had done everything asked of me, check the sound was active and the volume tujrned up, et al.

It was a pure accident that I nudged the volume control on the side of the laptop and voila sound......  Oh um.

However thanks for the speedy and knowledgable adviced and assistance.

I loves ubuntu now it all works.  I am sure I will have more dumbass questions as I progress :)

Thanks again

asathorny

---

