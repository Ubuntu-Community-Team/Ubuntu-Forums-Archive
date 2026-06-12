---
title: "Sound issues"
date: 2007-10-23
forum: Apple PPC Users
---

### Post by Auria on 2007-10-23
Hi,

i just installed Feisty (i was on a relatively stable Edgy for about a year, wanted to upgrade, and seeing how problematic gutsy seems to be i chose feisty)

i have a problem with sound however. It plays for a few seconds, sometimes i'm even able to play an entire ogg song, but sooner or later (and mostly within 10-20 seconds) the media player eventually freezes and from there i can never get any more sound. Programs designed specifically for audio mostly freeze or crash after it stops working. Yet it does work at the beginning.

I've had to disable ESD - no idea if it can be related.

The computer also fails to shut down (but perhaps because it tries to play some sound?)

Any help is appreciated - thanks.

---

### Post by frog_pilot on 2007-10-24
What hardware/ which mac do you use?

What is the output of ```
lsmod | grep snd
```.

Have a look at this [discussion]("http://ubuntuforums.org/showthread.php?t=551587").

---

### Post by Auria on 2007-10-24
ls_mod gives this:

> 
snd_powermac           49984  1 
snd_aoa_i2sbus         24292  0 
snd_pcm_oss            53984  0 
snd_mixer_oss          20960  1 snd_pcm_oss
snd_pcm                95812  3 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss
snd_page_alloc         11368  1 snd_pcm
snd_seq_dummy           4004  0 
snd_seq_oss            40660  0 
snd_seq_midi           10016  0 
snd_rawmidi            29632  1 snd_seq_midi
snd_seq_midi_event      8192  2 snd_seq_oss,snd_seq_midi
snd_seq                61888  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26404  2 snd_pcm,snd_seq
snd_seq_device          9388  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69812  12 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8996  1 snd
snd_aoa_soundbus        7812  1 snd_aoa_i2sbus


after trying to play a couple files, it however becomes:
> 
snd_powermac           49984  7 
snd_aoa_i2sbus         24292  0 
snd_pcm_oss            53984  0 
snd_mixer_oss          20960  1 snd_pcm_oss
snd_pcm                95812  6 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss
snd_page_alloc         11368  1 snd_pcm
snd_seq_dummy           4004  0 
snd_seq_oss            40660  0 
snd_seq_midi           10016  0 
snd_rawmidi            29632  1 snd_seq_midi
snd_seq_midi_event      8192  2 snd_seq_oss,snd_seq_midi
snd_seq                61888  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26404  5 snd_pcm,snd_seq
snd_seq_device          9388  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69812  18 snd_powermac,snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8996  1 snd
snd_aoa_soundbus        7812  1 snd_aoa_i2sbus


Why does the number next to snd_powermac increase?

I also tried the suggestions in the other thread, but no luck

---

### Post by frog_pilot on 2007-10-25
The second column shows the used memory in bytes. After playing some files, maybe it uses some more bytes. You have the same modules loaded as on my system, where sound is working with feisty (as stated, not as loud as with OS X). There is a bug on Ti Powerbook G4. You still didn't say, what hardware you use... Some infos about this bug are widespread in this [thread]("http://ubuntuforums.org/showthread.php?t=412151").

---

### Post by Auria on 2007-10-25
My computer is an eMac G4.

I'll take a look at the other thread yo posted when i get home

---

### Post by frog_pilot on 2007-10-26
On my system there is also esd disabled. Since then there ara no system sound on login and logoff. There is only this short drum sound when gdm starts.

In Audio-Prefrences I choosed ALSA for every channel and "PowerMac Snapper (Alsa Mixer)" for device.

Do you have the same audio settings?

---

### Post by Auria on 2007-10-26
> **frog_pilot said:**
> On my system there is also esd disabled. Since then there ara no system sound on login and logoff. There is only this short drum sound when gdm starts.

In Audio-Prefrences I choosed ALSA for every channel and "PowerMac Snapper (Alsa Mixer)" for device.

Do you have the same audio settings?

yes absolutely the same :(

i'll try following the advice in the other thread and downgrading the kernel - but meanwhile if you have any other idea...

---

### Post by Auria on 2007-10-26
Hey!

Following stmiller's advice here : [http://ubuntuforums.org/showthread.php?t=412151&page=5](http://ubuntuforums.org/showthread.php?t=412151&page=5)
seems to have solved the issue

thanks for providing the link :)

---

