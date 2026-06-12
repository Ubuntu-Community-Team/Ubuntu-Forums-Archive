---
title: "i have no sound....suddenly"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2007-12-11
hi everything was ok until the moment i reboot when i realized no sound anymore..
i think it might be after an update(something with the libs of 2d cairo clock...)
i really need sound... :(
any ideas?

---

### Post by sbodas on 2007-12-11
Did you check if your drivers are being loaded?  Try running "lsmod | grep snd" to see what you get.  Here's my output:

```
$ lsmod | grep snd
snd_pcm_oss            33440  0
snd_mixer_oss          12032  1 snd_pcm_oss
snd_seq_oss            26880  0
snd_seq_midi_event      4224  1 snd_seq_oss
snd_seq                36048  4 snd_seq_oss,snd_seq_midi_event
snd_seq_device          5004  2 snd_seq_oss,snd_seq
snd_intel8x0           22556  2
snd_ac97_codec         74020  1 snd_intel8x0
ac97_bus                1536  1 snd_ac97_codec
snd_pcm                54152  3 snd_pcm_oss,snd_intel8x0,snd_ac97_codec
snd_timer              15492  2 snd_seq,snd_pcm
snd                    33508  13 snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_seq,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
snd_page_alloc          6152  2 snd_intel8x0,snd_pcm

```

If your drivers are loaded, maybe a alsa restart will fix things too... you can try:
```

$ sudo /etc/init.d/alsa-utils restart

```

---

### Post by someoneouthere on 2007-12-11
my output
Code:
snd_rtctimer            4384  0 
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

and try restarting nothing...

---

### Post by sbodas on 2007-12-11
Did you check that your output channels aren't muted?  Check all your volume levels in kmix or alsamixer.

---

### Post by someoneouthere on 2007-12-11
checked still the same

---

### Post by someoneouthere on 2007-12-11
oh now i do listen but very low with the settings in the max

---

### Post by someoneouthere on 2007-12-11
and since the other channels were muted from the beggining except the internal speaker why now i have to configure them?

---

### Post by sbodas on 2007-12-11
Are the master and PCM channels maxed out?  I would guess that if your volume is low, the PCM may be set too low.  The reason you may get muted channels is that upgrading alsa drivers or other audio libraries sometimes messes up the mixer settings.

---

### Post by someoneouthere on 2007-12-12
so how can i fix it?

---

### Post by sbodas on 2007-12-12
What are your settings for the "Master" and "PCM" channels?  Are you sure that the settings of your external speakers haven't been touched?

Also, what audio is low?  Is it your system notifications or audio coming from Amarok (or whatever)?

---

### Post by someoneouthere on 2007-12-12
> **sbodas said:**
> What are your settings for the "Master" and "PCM" channels?  Are you sure that the settings of your external speakers haven't been touched?

Also, what audio is low?  Is it your system notifications or audio coming from Amarok (or whatever)?

if you mean the simple how low/high ihe volume all are in maximun
if you mean some other settings please give more details..

my sound is low from everywhere... rythmbox,xine radio firefox ,notifications...
i have them in max and the sound is like whispering...

---

### Post by sbodas on 2007-12-12
Do you have your Gutsy Live CD lying around?  If so, can you try booting into Gutsy from the livecd and checking how sound works there?

I have an HP laptop using the same hda-intel driver and it works fine for me.  If you do agoogle  search for "alsa low volume", you may find some pointers.  I saw this page:

[https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29%7C%28intel%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29%7C%28intel%29)

And this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93859](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93859)

It seems that putting the following line in /etc/modprobe.d/alsa-base fixed the problem for some users:
```

options snd-hda-intel model=auto

```

---

### Post by someoneouthere on 2007-12-12
i think the problem started after an update probably with the drivers...

---

### Post by sbodas on 2007-12-13
Did you try adding the options line to /etc/modprobe.d/alsa-base?  Also, I noticed this morning that libcairo2 was updated; you originally mentioned that your problems started after it was updated, so did it get fixed with the upgrade?

---

### Post by fuji on 2007-12-13
I have no sound too.  Maybe you have a kernel oops?  I have one preventing any application that attempts to use alsa freeze hard.  `kill -9`'s won't work.  I reported the bug here: [https://bugs.launchpad.net/ubuntu/+bug/175331](https://bugs.launchpad.net/ubuntu/+bug/175331)

Maybe a `dmesg | grep -i oops` command would show if you have the same thing?

---

### Post by someoneouthere on 2007-12-13
i'll give it a try but i think it is because i enabled the backports repository,installing beta drivers
how can i install the previous one through the software resources? (and unistall the present one)

---

### Post by sbodas on 2007-12-13
Just comment out the backports line in /etc/apt/source.list, run "apt-get update", and then you can downgrade whatever you need to.

Alternatively, you can manually downgrade the package in question using aptitude or synaptic.

---

