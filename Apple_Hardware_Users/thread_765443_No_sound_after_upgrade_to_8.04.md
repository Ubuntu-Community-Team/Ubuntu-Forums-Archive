---
title: "No sound after upgrade to 8.04"
date: 2008-04-24
forum: Apple Hardware Users
---

### Post by AlainJLEB on 2008-04-24
Hi there,

After a smooth upgrade from 7.10 to 8.04, I don't have sound anymore.

Alsa is still installed and the snd-hda-intel is detected, but impossible to have sound.

I have rebuilt & reinstalled alsa drivers, but still not working ... I have tried passing option
```
options snd-hda-intel model=imac24
```
in /etc/modprobe.d/alsa-base, but this does not help

Is there a way to find where the error is? There is an entry in /proc/asound for a Realtek ALC885 card ...

Alain

---

### Post by cyberdork33 on 2008-04-24
Please indicate what version iMac you have when posting.

Please check the levels in alsamixer.

Can you boot from the Hardy Live CD to see if sound is broken there too?

---

### Post by AlainJLEB on 2008-04-25
Don't understand ... this morning it's working fine :(

---

### Post by fakt00r on 2008-04-25
No sound here as well after upgrading. Upgraded MacBook (Santa Rosa) from Ubuntu 7.10 to 8.04. Solutions? :confused:

---

### Post by guj4_n3b3sk4 on 2008-04-25
Open shell and type only this line:

```
alsamixer
```

Navigate with right-left arrow between columns and rise all up to maximum with up arrow. After that just exit alsamixer and it should work. That's like most common problem with sound after upgrade. If it isn't that, let us know.

---

### Post by fakt00r on 2008-04-25
> **guj4_n3b3sk4 said:**
> Open shell and type only this line:

```
alsamixer
```

Navigate with right-left arrow between columns and rise all up to maximum with up arrow. After that just exit alsamixer and it should work. That's like most common problem with sound after upgrade. If it isn't that, let us know.

It's working again. :guitar: Thx!

---

### Post by Tamiyadd on 2008-04-25
> **fakt00r said:**
> No sound here as well after upgrading. Upgraded MacBook (Santa Rosa) from Ubuntu 7.10 to 8.04. Solutions? :confused:

hi have the same problem :( someone can help us? when i use this command 
```
rmmod snd_hda_intel
```

he says:
ERROR: Module snd_hda_intel is in use

why?

---

### Post by guj4_n3b3sk4 on 2008-04-25
> **Tamiyadd said:**
> hi have the same problem :( someone can help us? when i use this command 
```
rmmod snd_hda_intel
```

he says:
ERROR: Module snd_hda_intel is in use

why?

How about trying what I've suggested few posts above? Typing:
```

alsamixer
```

and incresing volume to maximum?

Try that.

PS: Why are you turning off that module, anyway?

---

### Post by Tamiyadd on 2008-04-25
> **guj4_n3b3sk4 said:**
> How about trying what I've suggested few posts above? Typing:
```

alsamixer
```

and incresing volume to maximum?

Try that.

PS: Why are you turning off that module, anyway?

i was following the guisty gibbon guide to make the sound work! i was reloading the module after making changes.
i don't know why but now the sound work! thank for the help!

---

### Post by hellmitre on 2008-04-25
I did that with alsamixer and it says, on the far right, above speaker, 00. I can't get any audio output through the speakers, though the major issue was the headphone jack, which now has audio. I'd say it's roughly 67% of my sound issue. Heh. Thanks. Any help on the speakers would be appreciated.

---

### Post by cyberdork33 on 2008-04-25
> **hellmitre said:**
> I did that with alsamixer and it says, on the far right, above speaker, 00. I can't get any audio output through the speakers, though the major issue was the headphone jack, which now has audio. I'd say it's roughly 67% of my sound issue. Heh. Thanks. Any help on the speakers would be appreciated.pressing 'm' while on a channel to mute/unmute it

---

### Post by Mike Kimmick on 2008-04-25
There seems to be a variety of issues causing sound problems with newer version of Ubuntu.

Anyway, here's my two cents...

I have an Acer Aspire 5050 3242 laptop, and I just installed Hardy Heron.  What a surprise, I don't have any sound.

This laptop has an ATI SB450 sound card (built-in) and the chipset is ALC883.  After finding a bug report (sorry, I don't remember the ticket number) and then reading the alsa docs (the INSTALL file included with alsa-driver tarball), I found some options that could be added to /etc/modprobe.d/alsa-base.

The one option that _should_ work but doesn't is
options snd-hda-intel model=acer

And the one that works and is listed in the bug report is
options snd-hda-intel model=auto

I added this option to /etc/modprobe.d/alsa-base, rebooted, and now I have sound.

Hope this helps somebody!

Regards,

Mike Kimmick

---

### Post by mindmanmusic on 2008-05-17
I too had no sound after upg to 8.04 on imac with Screamer card.
ran alsamixer and ran the volumes up, and still no sound, so i decided to try some headphones on the audio out port on the side of the imac, when i unplugged the headphones, voila it all started working! wierd, but i guess the headphone detection kicked in!
WOOT

---

### Post by Bakyt Niyazov on 2008-06-02
Hello!

I've upgraded my Kubuntu Gutsy to Hardy nicely.
There are many great improvements in Sound system also!
My multimedia keyboard is working!!!

But only in built in speakers working (of notebook)
When I plug my headsets - no sound. Help!

I've increased all the possible volumes.

BTW When I ran **alsamixer**
There is second column called Headphon (yes exactly Headphon)
the it is on 00 position. And I can't increase it.

Be assured my headsets works great!

---

### Post by papsynot on 2008-08-06
I've got exactly the same situation as Bakyt on my new Asus laptop.
My settings (from System -> KInfoCenter -> Sound):

Sound Driver: 3.8.1a-980706 (ALSA v1.0.16 emulation code)

Installed drivers:
Type 10: ALSA emulation

Card config:
HDA Intel at 0xfebf8000 irq 23
HDA ATI HDMI at 0xfdeec000 irq 17

Audio devices:
0: ALC861VD Analog (DUPLEX)

I was also wondering why I can't increase the Headphone volume setting in alsamixer.

Tried plugging in the headphones and raising the volume setting then, but again no luck. 

Also added that line to modprobe.d/alsa-base, but still audio is not working for me. 

Thanks in advance!

---

### Post by cyberdork33 on 2008-08-06
> **papsynot said:**
> I've got exactly the same situation as Bakyt on my new Asus laptop.
This is an Apple forum...

---

### Post by Geeb on 2008-10-30
> **mindmanmusic said:**
> I too had no sound after upg to 8.04 on imac with Screamer card.
ran alsamixer and ran the volumes up, and still no sound, so i decided to try some headphones on the audio out port on the side of the imac, when i unplugged the headphones, voila it all started working! wierd, but i guess the headphone detection kicked in!
WOOT

Thanks mindmanmusic this worked for me in Kubuntu 8.1 on my iMac.  I had to plug in the headphones, play with the mixer and everything worked.

---

