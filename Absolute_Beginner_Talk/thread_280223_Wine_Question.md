---
title: "Wine Question"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2006-10-19
Cheers,

I just recently installed Ubuntu on my pc (about 1 month now).  And as soon as I installed it, one of the first thing I installed is wine.  I use mainly wine for running uTorrent (because Azureus is just not working for me) and 7Zip.  My question is that when I type winecfg in terminal the wine configuration appears but when I move to the audio tab the wine configuration just quits on me and on my terminal window I see this:

delphiguy@zion:~$ winecfg
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/delphiguy/.kde/socket-zion.
can't create mcop directory

What does this mean? does this mean that I can't have sound on my applications running wine?  And why does it look on .kde folder when I have gnome as my desktop?

Thanks.

---

### Post by KuriKai on 2006-10-19
type this in a terminal
sudo modprobe snd-seq-midi = creates /dev/snd/seq
does it work now?

---

### Post by delphiguy on 2006-10-19
Doing the command above I get this:

FATAL: Error inserting snd_seq (/lib/modules/2.6.15-27-386/kernel/sound/core/seq/snd-seq.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_seq
WARNING: Error inserting snd_seq_midi_event (/lib/modules/2.6.15-27-386/kernel/sound/core/seq/snd-seq-midi-event.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_seq_midi (/lib/modules/2.6.15-27-386/kernel/sound/core/seq/snd-seq-midi.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

