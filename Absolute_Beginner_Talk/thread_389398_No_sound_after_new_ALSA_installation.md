---
title: "No sound after new ALSA installation"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by mahy on 2007-03-20
Hi folks,

i installed the newest ALSA drivers in vain hope to get my microphone to work. Naturally i got no sound at all as a result. When i try modprobe snd-hda-intel, this is the result:

WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.17-11-generic/kernel/sound/acore/snd-page-alloc.ko): Invalid module format
FATAL: Error inserting snd (/lib/modules/2.6.17-11-generic/kernel/sound/acore/snd.ko): Invalid module format
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.17-11-generic/kernel/sound/acore/snd-timer.ko): Invalid module format
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.17-11-generic/kernel/sound/acore/snd-page-alloc.ko): Invalid module format
FATAL: Error inserting snd (/lib/modules/2.6.17-11-generic/kernel/sound/acore/snd.ko): Invalid module format
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.17-11-generic/kernel/sound/acore/snd-timer.ko): Invalid module format
FATAL: Error inserting snd_pcm (/lib/modules/2.6.17-11-generic/kernel/sound/acore/snd-pcm.ko): Invalid module format
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.17-11-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Invalid module format
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.17-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Invalid module format


Ideas, anyone? How do i at least revert to the packaged drivers? TIA

---

### Post by rennen01 on 2007-03-21
That has happened to me before.  I did this:

[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

In the "Getting the ALSA drivers from a *fresh* kernel" Section.

GL.

---

### Post by mahy on 2007-03-22
Thanks a lot, but there was a different problem. When ALSA was checking the gcc, it found out the highest version is 4.1, but the outcome of 'gcc -v' would show that 4.0 is the default version. So ALSA designed all the makefiles for 4.1 version, but used the 4.0 version to compile everything.

So i had to do 'make uninstall', remove the gcc-4.0 packages, adjust the symlinks /usr/bin/gcc and /usr/bin/cc so that they point at /usr/bin/gcc-4.1 and it helped! Not only ALSA compiled correctly, but also worked after reboot! :) I love you, Tux the penguin. :KS

---

### Post by thefoolisme on 2007-03-22
Would you mind posting how you made the "uninstalls"?  If you look through the board, you'll notice that there are a lot of sound issues all of a sudden.  I'm beginning to think that there was a bug in the last update, because updating is all we all seem to have in common.  Knowing how to back track out of that update would be good.  :-)

---

