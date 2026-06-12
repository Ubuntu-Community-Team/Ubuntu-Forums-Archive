---
title: "alsamixer broken?"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by jaredssix on 2008-03-06
Hey all, 

Two things:

1. My alsamixer is gone! Here is the terminal output:
```

ALSA lib control.c:874:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory
```

I uninstalled and reinstalled from Syaptic, to no avail.

2. I'm guessing this might be related to my recent loss of microphone ability--what worked two days ago, no longer works! I've perused the forums and there doesn't seem to be a solution to ```
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

```

I'll add that response to terminal input "vumeter -r &" (to test the mic) is a gui stating "Cannot connect sound to daemon. Please run 'esb' at a command prompt."

which is the result of System-->Preferences-->Sound-->Sound Capture/Test


I'm thinking of reinstalling Gutsy to see if the mic works (like it did two days ago).

Ideas?

---

### Post by S15_88 on 2008-03-07
what happens when you type in alsamixer at the terminal?

---

### Post by jaredssix on 2008-03-07
I got the code listed beside 1) above.

I ended up reinstalling Gutsy, and now I'm good to go.

I don't suppose that makes this thread "solved", just dealt with.

Thanks!

---

