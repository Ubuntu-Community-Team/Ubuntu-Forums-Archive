---
title: "Wierd noise"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by Z Quickfire on 2006-12-21
I just started using Ubuntu but when I do my computer makes kind of a high pitched buzzing sound. I haven't heard this with windows and it is a little bit annoying. Does anyone know what causes this? Thanks!

EDIT: Weird, not wierd.

---

### Post by scrooge_74 on 2006-12-21
There is a thread about it, it happen to someone a few days ago.  Uninstall ALSA, then reboot and install again that should clear it up.

You probably mess something up so this is going to be easier and take less time

---

### Post by Z Quickfire on 2006-12-21
> **scrooge_74 said:**
> There is a thread about it, it happen to someone a few days ago.  Uninstall ALSA, then reboot and install again that should clear it up.

You probably mess something up so this is going to be easier and take less time

ALSA?

---

### Post by scrooge_74 on 2006-12-21
> **Z Quickfire said:**
> ALSA?

ALSA is the sound system

Go into synaptic and tell it to remove alsa, afterwards you can reinstall it and it will be back at the default settings.

Let me see if i can find the original thread from a few days back

---

### Post by Z Quickfire on 2006-12-21
Ok thank you.

---

### Post by Z Quickfire on 2006-12-21
> **scrooge_74 said:**
> ALSA is the sound system

Go into synaptic and tell it to remove alsa, afterwards you can reinstall it and it will be back at the default settings.

Let me see if i can find the original thread from a few days back

Also, do I need internet access to reinstall it? My wireless card apparently does not work with ubuntu, so currently I can only connect via Windows XP.

---

### Post by scrooge_74 on 2006-12-21
alsa comes as part of the CD install.  Also if you boot from Live CD you should not have any sound problem and that will tell you it is bad config on the installed system

Have you also try using your wireless card using the Live CD? if the live CD detects it then you  should be ok.

also you can use ndiswrapper to configure your windows drivers for the card under linux (but this is only if you can't find linux drivers

EDIT: this is the thread with a similar problem in it for the sound system [http://ubuntuforums.org/showthread.php?t=314700](http://ubuntuforums.org/showthread.php?t=314700)

---

### Post by jimrz on 2006-12-21
> **Z Quickfire said:**
> Also, do I need internet access to reinstall it? My wireless card apparently does not work with ubuntu, so currently I can only connect via Windows XP.

which cd did you use for your install?

i beleive that ALSA will be on your ubuntu cd and, therefore you should be able to use Synaptic for this without internet connect


EDIT:  too slow again

---

### Post by scrooge_74 on 2006-12-21
Check the last post of the thread I sent you, it may be that you have to mute the mike in the sound mixer and it is giving you feedback

---

### Post by Z Quickfire on 2006-12-21
I used the 6.10 LiveCD I downloaded for install, and I believe I was hearing the sound there as well.

---

### Post by scrooge_74 on 2006-12-21
Check the mic it may be the culprit it could be enable at full as the other thread says

---

### Post by Z Quickfire on 2006-12-21
Ok thank you, I'll try all these things when I get back on to Ubuntu.

---

