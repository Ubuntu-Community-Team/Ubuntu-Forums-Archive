---
title: "No sound on beige G3"
date: 2005-12-09
forum: Apple PPC Users
---

### Post by ristosu on 2005-12-09
I've managed to install Warty on my beige G3. I boot with BootX. It seems usable, if I only could get some sound out of it. I tried with CD player, and it plays silently without a problem. I have the following alsa drivers loaded:

snd_powermac           44304  6
snd_pcm_oss            68136  0
snd_mixer_oss          23264  4 snd_pcm_oss
snd_pcm               119800  2 snd_powermac,snd_pcm_oss
snd_page_alloc         13480  1 snd_pcm
snd_timer              29348  1 snd_pcm
snd                    67800  11 snd_powermac,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11812  4 snd

I tried to adjust volumes with the mixer, but it didn't help. Any ideas?

More: Now i got sound from Rhythmbox, after adjusting H channel in mixer. I wonder what that H means... This was on OSS tab. On Alsa tab PC Speaker had similar function. Neither on them helps with CD player.

So it's just CD player's problem. Maybe I should check that there is an audio cable from the CD drive to the motherboard... But is it needed? It works in Mac OS. Has anyone played CD's successfully with Warty on a beige G3?

Finally: selecting line in and volume as recording sources and adjusting inf and amp master (and maybe something else) helped.

---

