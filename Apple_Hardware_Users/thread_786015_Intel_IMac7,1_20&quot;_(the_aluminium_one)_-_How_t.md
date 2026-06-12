---
title: "Intel IMac7,1 20&quot; (the aluminium one) - How to get sound on 8.04 (Hardy Heron)"
date: 2008-05-07
forum: Apple Hardware Users
---

### Post by blurg on 2008-05-07
Hi,

To get sound on Ubuntu 8.04 Hardy Heron on my iMac7,1 20" (the new aluminium one) add the following line to the end of:

/etc/modprobe.d/alsa-base

```
options snd-hda-intel model=imac24
```

Then reboot and should be working :)

Note that I'm on an iMac 20" but there is no code for that and obviously the sound is the same as the iMac 24" (if you doube click the volume icon on top right then go File->Change Device-> you should see mention of Realtek ALC885, if not this is probably not the correct fix for you!)

Hope that helps folk - I got a shock when I heard to default login sound for the first time after reboot!

---

### Post by magic-neophyte on 2008-08-03
Thanks, this worked for me and is far easier than recompiling alsa 1.0.15.

---

### Post by oneiric on 2009-03-31
hi,

Thanks for this solution.  It fixed my sound issues on an Intel iMac7,1 with sound card Intel Corporation 82801H (ICH8 Family) HD Audio Controller


Sound is working, but nothing comes out of the headphone jack. Anyone figured that part out?

---

### Post by jeffmings on 2009-04-14
Hello!

I submitted a bug report for this issue as [https://bugs.launchpad.net/bugs/360866](https://bugs.launchpad.net/bugs/360866) . I hope we can get this resolved. I have been using Linux as my OS of choice since Redhat 5.1, and would love to be able to enjoy good sound running Jaunty Jackalope on my aluminum iMac :p

Aloha,
-Jeff Mings

---

