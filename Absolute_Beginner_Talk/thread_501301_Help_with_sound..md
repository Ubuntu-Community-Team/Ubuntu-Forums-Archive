---
title: "Help with sound."
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by jorpe on 2007-07-15
I've installed Mplayer and belonging codecs...
and then the sound were gone the day after, didn't restart and some thing like that..

anyway, [http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-feisty-fawn.html) there is were I found the codec package.. 

How to get my sound back help plz?..

/jonas

---

### Post by bliffle on 2007-07-15
What equipment do you have?

Did the audio work before you installed the codecs?

Have you tried "System...preferences...sound" from the uppermost menubar? Could you test the enabled sounds?

Have you opened a "Terminal" session , typed "alsamixer" and experimented with the level settings?

I've done all that on my IBM Thinkpad T40 with Feisty 7.04, and now I get a really weak sound, barely audible. And sometimes the sound amp oscillates and squeals until I turn it down.

---

### Post by jorpe on 2007-07-15
The weird thing is that the sound worked perfectly at first.. but the next day the sound were gone.. 

Ubuntu Feisty 7.04 ASUS intergrated soundcard Realtek channel 6 or something... if you mean that?.

So I started to search for  drivers "alsa" I guessed was a sound driver so I erased it and tried to reinstall but it didn't work...
Maybe I messed this up again =p

When I try to test the sound an error message appears [PHP]gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Resource not found.[/PHP]

When I go to the terminal another message appears [PHP]jorpe@jorpe-desktop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device[/PHP]

Thx for the answer.!

---

### Post by jorpe on 2007-07-15
Btw, one error message says that Gstreamer is missing.. 

[PHP]No volume control GStreamer plugins and/or devices found.[/PHP]

Is that what im missing maybe not the sound drivers...

/jorpe

---

### Post by expatCM on 2007-07-15
Do you have two sound cards on this computer?

At the command line would you please type 

```
asoundconf list
```

What does it say?

---

### Post by jorpe on 2007-07-15
Okey, I reinstalled Ubuntu.. now the sound works again...

=p thx for the help anyway.

---

