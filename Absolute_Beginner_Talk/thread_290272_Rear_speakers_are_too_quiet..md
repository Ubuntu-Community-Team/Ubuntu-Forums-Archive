---
title: "Rear speakers are too quiet."
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Yes_It's_Me on 2006-11-01
Hi, I searched for this but nothing has really helped so far.

I just today, after months upon months of frustration FINALLY got my rear speakers working for Ubuntu!

But there is still a problem, my rear speakers (logitech X-530) work but are much quieter than the front ones, everything in alsamixer is on and on max. For some reason the master volume only changes the front speaker volume, not the rear, the rear speakers only adjust if i alter the "surround" slider (this doesn't affect the front ones). If I put my master on ~half and everything else on high the balance is good but because the master is not on full my speakers have to be up really high to get decent overall volume, which is a problem if I change into XP without changing it (gives you a heart attack!).

Anyway, Is there some way I can change a file or setting to amplify the rear speakers? Cheers.

PS. Also, when I run speaker-test surround51 -c6 in the terminal I get:

"speaker-test 1.0.11

Playback device is default
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 3 to 5461
Period size range from 3 to 5461
Using max buffer size 5461
Periods = 4
was set period_size = 5461
was set buffer_size = 5461
buffer to small, could not use
Unable to determine current swparams for playback: Input/output error
Setting of swparams failed: Input/output error"

---

### Post by NeoLithium on 2006-11-01
Have you tried running ```
alsamixer
``` in a terminal window? You should be able to adjust the baseline speaker volume from there.

---

### Post by Yes_It's_Me on 2006-11-01
tried that, everything is on max, played around in that for ages.

thanks.

---

### Post by Claus7 on 2006-11-05
Hi,

it was really helpfull the [COLOR="Red"]alsamixer[/COLOR] command. I have a soundbaster Live 5.1! sound card and I had to configure the wave surround in alsamixer in order to have my rear speakers working. Yet, I have a small problem. A [COLOR="Red"]weird sound[/COLOR] periodicaly is heard while I'm hearing
mp3's or not (it's like a guitar's sound). Does anyone know how to deactivate this feature?

I want also to point out that in order for someone to listen to mp3's, the codecs from add/remove applications are needed (for Daper Drake).

---

### Post by Claus7 on 2006-11-18
Hi,

It had to do with the reminders (that weird sound I was referring). For example, if you had opened aMSN, and you were looking on another window, this sound was heard in order to remind you that someone had sent a message to you. We all start from the beginning, sometime!

---

