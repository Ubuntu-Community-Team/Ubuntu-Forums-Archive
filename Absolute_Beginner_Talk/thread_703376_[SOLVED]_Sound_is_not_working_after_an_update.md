---
title: "[SOLVED] Sound is not working after an update"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by XVII on 2008-02-21
I have tried plugging in head phones and using different speakers, so I know they aren't the problem.  I did some searching but couldn't find an answer.

I updated my system this morning with these updates:

```

Commit Log for Thu Feb 21 07:43:53 2008


Upgraded the following packages:
libcdio6 (0.76-1ubuntu2) to 0.76-1ubuntu2.7.10.1
libiso9660-4 (0.76-1ubuntu2) to 0.76-1ubuntu2.7.10.1
libqt4-core (4.3.2-0ubuntu3.1) to 4.3.2-0ubuntu3.2
libqt4-gui (4.3.2-0ubuntu3.1) to 4.3.2-0ubuntu3.2
libqt4-qt3support (4.3.2-0ubuntu3.1) to 4.3.2-0ubuntu3.2
libqt4-sql (4.3.2-0ubuntu3.1) to 4.3.2-0ubuntu3.2
qt4-qtconfig (4.3.2-0ubuntu3.1) to 4.3.2-0ubuntu3.2

```

and my sound stop working completely.

My sound card is detected however.  Here is the output of ```
aplay -l
```

```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

All help is appreciated. I have a project I need to finish this weekend and sound is a crucial part of it.

---

### Post by pedro_orange on 2008-02-21
Might be totally obvious....

But have you tried using the different sound drivers: oss/alsa etc?

If so, and that didn't work. maybe the sound is being locked by a process, and therefore a reboot would probably be the best option and see if it works then.

Other than that, I would recommend asking in the Sound section of this forums, perhaps they can help you more.

---

### Post by XVII on 2008-02-21
I went under System>Preferences>Sound and tested out all of the different options.  Only the OSS option has any output, but when I choose OSS and then try to play any sound there is no output.

EDIT:

OK, I solved my problem.  For people having a similar problem to mine, this is what I did:

I uninstalled these packages:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```

Then I reinstalled them:
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```

Then, It removed some packages as a side effect that I had to reinstall them:
```

sudo apt-get install gdm ubuntu-desktop

```

Then I rebooted and ran alsamixer and made sure nothing was muted and cranked all of the volumes up to max.

I hope that this will help some people.

---

### Post by ronbently on 2008-02-24
Thanks for your insight here. Another thread was recently started about this and I will point them here.

---

### Post by bruban on 2008-04-03
> **XVII said:**
> I went under System>Preferences>Sound and tested out all of the different options.  Only the OSS option has any output, but when I choose OSS and then try to play any sound there is no output.

EDIT:

OK, I solved my problem.  For people having a similar problem to mine, this is what I did:

I uninstalled these packages:


</snip>

[

I tried your suggestion but no luck.

I'm running Ubunutu 7.10 i386.

My sound stopped working after a recent system update.

I've noted a number of reports with similar symptoms, particularly sound stopping to work after a recent update.

Does anyone have any ideas on how to fix this?

---

### Post by XVII on 2008-04-04
> **bruban said:**
> I tried your suggestion but no luck.

I'm running Ubunutu 7.10 i386.

My sound stopped working after a recent system update.

I've noted a number of reports with similar symptoms, particularly sound stopping to work after a recent update.

Does anyone have any ideas on how to fix this?

I have no idea, you will have to be more specific; also, this is a solved thread, you will probably have better luck posting a thread of your own.

---

