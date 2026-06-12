---
title: "No audio on 27'' Core 2 Duo late 2009 iMac"
date: 2010-01-07
forum: Apple Hardware Users
---

### Post by drewx on 2010-01-07
I've been going at this for a while, trying to find the magical recipe of setting that will allow me to hear sound on this machine when it's running Ubuntu. So far my attempts to play around with alsa-base.conf's model option and to upgrade to the latest version of alsa-driver have been met with resounding silence.

Does anyone out there have the magical formula?

Thanks so much, guys. The community is what makes Ubuntu great.

Andrew

---

### Post by linuxopjemac on 2010-01-07
did you unmute all channels with alsa-mixer ?

---

### Post by linuxopjemac on 2010-01-07
what you can also try is to use the backports alsa module:

```
aptitude update
aptitude install linux-backports-modules-alsa-karmic-generic
```

please let us know if that works

PS as you can see [here]("http://bugtrack.alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.22.1"), the latest snapshot of ALSA gives a working iMac 27". So, if you install the above backported alsa-module, it should work.

---

### Post by drewx on 2010-01-07
All channels unmuted. Installed the backport. still no sound. My chip is reading as Cirrus Logic CS4206 in alsamixer, which doesn't sound right. It used to say a different chip type, and I'm wondering what has changed and if that's part of the issue.

Thanks for the continued help.

---

### Post by linuxopjemac on 2010-01-08
you can try to add model=imac27, model=mbp55 or model=auto at the end of the /etc/modprobe.d/alsa-base.conf, as I have seen in [this thread]("http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt") that it uses the same chipset.

---

### Post by drewx on 2010-01-08
Oddly, when I created a new user, everything started working. No idea why. Thanks for all your help and sorry for the hassle. Now if I could only figure out how to make Ubuntu send a reboot signal that this machine interprets correctly...

---

### Post by drewx on 2010-01-11
Well I ran some updates (including an update to the ALSA backport) and sound is gone again. Any ideas?

---

### Post by drewx on 2010-01-11
OK, working again. I had to uninstall and reinstall alsa-base and then the backport. All's well. And looks like one of the new updates fixed the reboot issue, too. So I'm almost done now. Phew.

---

### Post by linuxopjemac on 2010-01-11
nice to hear!

---

### Post by ZeroLinux on 2010-03-09
And what about integrated mic? Does it work?

---

### Post by Atilana on 2010-03-10
I had to uninstall and reinstall alsa-base and then the backport. All's well. And looks like one of the new updates fixed the reboot issue, too. So I'm almost done now.

---

### Post by ZeroLinux on 2010-03-17
Does the integrated microphone work with Skype, for example, with the normal sensitivity?

---

