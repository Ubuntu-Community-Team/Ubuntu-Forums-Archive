---
title: "Flash + Firefox = No Sound"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by Inkyskin on 2006-01-27
I have FF 1.5, and the latest version of flash, but I seem to have lost all sound from any kind of flash, any ideas on a fix?

---

### Post by cwaldbieser on 2006-01-27
[QUOTE=Inkyskin]I have FF 1.5, and the latest version of flash, but I seem to have lost all sound from any kind of flash, any ideas on a fix?[/QUOTE]
Edit /etc/mozilla-firefox/mozilla-firefoxrc and see if you have something like:
```

# which /dev/dsp wrapper to use
FIREFOX_DSP="auto"

```
You need to change it to your sound system.  I use aRTs for KDE, so mine looks like:
```

# which /dev/dsp wrapper to use
FIREFOX_DSP="artsdsp"

```

---

### Post by Inkyskin on 2006-01-27
Thanks :) But how do I find out which sound system I have? (I = noob)

---

### Post by hen3rz on 2006-01-27
Hi cwaldbieser,

I was wondering if your solution would also fix a problem I'm having with firefox 1.5. Any flash file that is loaded in firefox plays at maximum volume and I cant turn it down using my volume button on the top right? If it will fix my problem I'm in the same boat as Inkyskin. 

> Thanks  But how do I find out which sound system I have? (I = noob)

---

### Post by bfonseca on 2006-01-27
try the lsmod command. Some names are often cryptic but some are recognizable.
brian

---

### Post by jrib on 2006-01-27
[QUOTE=Inkyskin]I have FF 1.5, and the latest version of flash, but I seem to have lost all sound from any kind of flash, any ideas on a fix?[/QUOTE]
i don't think firefox1.5 will use /etc/mozilla-firefox/mozilla-firefoxrc (I believe it was a modification made by ubuntu to the firefox included with ubuntu).

There are two threads though that take care of this sound problem though.  Best is to read through both of them:
[http://ubuntuforums.org/showthread.php?t=101438](http://ubuntuforums.org/showthread.php?t=101438)
[http://ubuntuforums.org/showthread.php?t=76743](http://ubuntuforums.org/showthread.php?t=76743)

[QUOTE=hen3rz]Hi cwaldbieser,

I was wondering if your solution would also fix a problem I'm having with firefox 1.5. Any flash file that is loaded in firefox plays at maximum volume and I cant turn it down using my volume button on the top right? If it will fix my problem I'm in the same boat as Inkyskin.[/QUOTE]

Try double clicking on the icon and changing the PCM volume

---

### Post by cwaldbieser on 2006-01-27
[QUOTE=Inkyskin]Thanks :) But how do I find out which sound system I have? (I = noob)[/QUOTE]
Well, I think Ubuntu uses esd or alsa by default.  If you look at the process table and find esd in it, you are probably using esd.  If you are using Kubuntu, you are probably using aRTs.  Otherwise, you are probably using alsa.

(This shows if esd is running).
```

$ ps aux | grep esd

```

---

### Post by cwaldbieser on 2006-01-27
[QUOTE=_jason]i don't think firefox1.5 will use /etc/mozilla-firefox/mozilla-firefoxrc (I believe it was a modification made by ubuntu to the firefox included with ubuntu).
[/QUOTE]
Hmm, well it is just a bunch of environment variables passed to the program.  I guess you could try something like:
```

$ FIREFOX_DSP="none" firefox

```
That would run it with whatever value you set for the variable.  I don't have 1.5, so I am not sure if it will respect that variable or not.

---

### Post by Inkyskin on 2006-01-28
Thanks cwaldbieser, it was esd :) Now I can hear everything fine again :)

---

