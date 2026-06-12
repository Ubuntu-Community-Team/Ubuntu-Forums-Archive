---
title: "Problems with Wine installation"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2006-12-31
Ok, downloaded Automatix and got it up and running. Installed a few programs and things went very smooth, until I tried to install Wine. Did the winecfg in terminal but all I get in response is this "ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet". Any ideas as to what I can do?? Thanks in advance and Happy New Year.

---

### Post by tchoklat on 2007-01-02
exactly the same for me


tchoklat

---

### Post by energiya on 2007-01-02
It works for me, even thow I get
> fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

Read a few months ago something about this... not so important

...after a ls /dev/snd I get
> controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1c  pcmC0D1p  seq  timer


You could try using OSS as your system default and see if it works

---

