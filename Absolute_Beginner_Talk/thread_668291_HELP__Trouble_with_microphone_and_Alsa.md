---
title: "HELP:  Trouble with microphone and Alsa"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Michl on 2008-01-15
I have searched I think through every file on microphone trouble and tried
everything, but cannot solve my problem, mainly to get myUSB  microphone and
sound to work with skype in Feisty.

Here is relevant info:

First, I can record with the Sound Recorder, although with some funkiness.
I cannot 'save' (get a message about invalid parameters), but using 'save as'
I can save and then playback.

Second, in Preference -> Sound -> Devices the sound playback in all three
categories tests ok in autodetect and OSS, but not in ALSA or Intel 82801AA.
So it uses OSS instead of ALSA, which seems to be a problem.

Third, in Preference -> Sound -> Sounds I when I hit PLAY for where there
is supposed to be a sound, I get silence.  In Edgy, I had a sound there, but
not now in Feisty.  HOWEVER, I do have system sounds and playback otherwise.

Fourth, when I do
```
vumeter -r &
```
in the terminal, I get a message that it cannot connect to the sound daemon, that I should run esd, and in the terminal there is lots of text about error and unable to find defintions.

When I run esd, I get 
```
SA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM dmix:I82801AAICH

```

I have attached a screenshot of the processor info:
/home/ml/Desktop/Screenshot--proc-asound.png

Hope someone can help!!!!!

---

