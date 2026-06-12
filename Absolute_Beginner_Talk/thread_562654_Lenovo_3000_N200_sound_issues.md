---
title: "Lenovo 3000 N200 sound issues"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by antooine on 2007-09-29
I just bought a lenovo n200 laptop, and my sound doesn't work. How do I go about findng out why my sound doesn't work and more importantly how can i use that information to fix it.

Just so people know, it's a Celeron 1.86 GHz, and when I first installed feisty I had issues with X, my wireless, my sound and Feisty won't mount my DVD drive. I've fixed the two problems but require help on the others. It's an 82801H HD Audio Controller, tf that means anything.

---

### Post by antooine on 2007-09-29
just an update, when I ran the following command : lsmod | grep snd

I got the following feedback

snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm

---

### Post by Daveth on 2007-09-29
may be something in here to help you

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo_IBM](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo_IBM)

---

### Post by antooine on 2007-10-02
n200 isn't listed but n100 is.

---

### Post by niels_mit_e on 2007-11-01
Hi there!
Try to do the following, after this my sound worked:

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768)

and then you still need (before rebooting) to do the following:

"Sound does not work out-of-the-box, but this is simply fixed by adding the following to etc/modprobe.d/alsa-base

options snd-hda-intel single_cmd=1 model=lenovo"

from user chrismyers ([http://ubuntuforums.org/showpost.php?p=3621959&postcount=8](http://ubuntuforums.org/showpost.php?p=3621959&postcount=8))

Good Luck!

---

### Post by Thulemanden on 2007-12-08
I suppose the character " is missing

options snd-hda-intel single_cmd=1 model=lenovo"

and the correct is

options snd-hda-intel single_cmd=1 model="lenovo"

it worked for me. Thanks for the solution. :)

---

### Post by persiangulf on 2008-01-01
But It did not work for me.
My laptop is lenovo n200 0769 b2g.

---

### Post by monkeyking on 2008-01-02
have you tried upping, and unmuting the volume?

---

### Post by persiangulf on 2008-01-03
As it seems, the sound work but there is no output sound. You can change the volume but the problem is that you can not hear any thing.

---

### Post by persiangulf on 2008-01-11
Is there any body to answer my question?:confused:

---

### Post by CazperII on 2008-01-11
@persiangulf I have the same type of n200, and the fix worked fine. The only issue I still have with the sound is that it doesn't mute when plugging in the headphone jack.

---

### Post by swoveck on 2008-03-15
Hi, 
I spent some time on searching the solution for internal speakers mute/unmute problem, but the solution that actually works for me happened to be much simpler that i supposed :). You just mute the "Front" in Alsa Mixer (if you don't have it just check it under Edit->Preferences), and then the signal goes just to headphone jack (you have to have "Headphones" checked under "Switches" tab) It's not automatic though, but for me at least it's enough since i have the headphones connected all the time.

---

### Post by CazperII on 2008-03-16
yep that's how I am working around the headphone/mute bug. I read somewhere that the issue is going to be resolved with the next release of ALSA. Or maybe the Hardy release in april is going to make a diffrence? Let's hope so.

---

