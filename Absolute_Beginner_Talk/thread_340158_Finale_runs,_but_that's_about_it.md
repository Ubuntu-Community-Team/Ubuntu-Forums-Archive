---
title: "Finale runs, but that's about it"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by k1001001 on 2007-01-16
I used wine to install Finale Notepad. It's up and running, which is a first for me trying to install a program using wine. However, you can't select what note value you want, the system responses are slow, and playback is very choppy. It's pretty much useless at this point.

Something that might help:
When I run winecfg, and go to the Audio tab, I get this error message:
```
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card 'default'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
```
So I try running JACK, but this doesn't seem to help.

Also, attached is a screenshot. Note the greyed-out options on the toolbar. I can't select anything but eighth notes.

In addition, when I close Finale, I get an incessant error message saying "One or MIDI devices are not responding." This message will not go away either, so I just have to put it over in another workspace.

Any ideas as to what the problem could be?

---

### Post by WiseElben on 2007-01-16
The same happens to me. I think it would be just better to compose on an XP or Mac, as trying to load up virtual instruments and such would not work too well on Wine. It's just to resource intensive and complex.

---

### Post by muusikko on 2007-01-17
You have to write in terminal:
sudo ln -s /usr/lib/libjack-0.100.0.so.0 /usr/lib/wine/libjack.so

then run winecfg from terminal
in the sound tab select OSS-driver and DirectSound with following settings Full - 44100Hz -16bit

These settings worked best for me, the sound is clear and playback quite fast. I have Finale 2005. But there's still some bugs:
[http://bugs.winehq.org/show_bug.cgi?id=6517](http://bugs.winehq.org/show_bug.cgi?id=6517)
[http://bugs.winehq.org/show_bug.cgi?id=6516](http://bugs.winehq.org/show_bug.cgi?id=6516)
which are very annoying.

And for example when I use the resize tool in whole page, the result is different (worse) as in WinXp. So I have to do the "final" editing allways in XP. And I can't print in wine.
I'd like to buy Mac, but money..

---

