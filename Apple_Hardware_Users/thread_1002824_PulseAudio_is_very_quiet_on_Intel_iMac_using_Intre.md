---
title: "PulseAudio is very quiet on Intel iMac using Intrepid"
date: 2008-12-05
forum: Apple Hardware Users
---

### Post by tedrogers on 2008-12-05
Hi all,

I've followed the PulseAudio HowTo guide below and it did not fix the problem for me.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I can hear the sound, but it is so incredibly low.

It also only seems to work on the headphone output, although the mac speakers might just not being driven hard enough to hear.

I've followed every guide I can find, all my volumes are up on both the PulseAudio and Alsamixer. Nothing is muted and no digital outputs are enabled (this sometimes mutes analogue outputs and I've been caught out with this in the past on other machines / laptops).

What can I do here to get this working?

Thanks.

---

### Post by smartbei on 2008-12-05
Have you tried right-clicking on the volume control applet and selecting Open Volume Control, and then turning everything up?

That actually fixed my problem, which sounds similar to yours. For some reason it shows things that alsamixer does not.

---

### Post by tedrogers on 2008-12-05
Thanks for the speedy reply.

Yes, sorry, I should have made that clear.

I have turned up all *relevant* channels on alsamixer and on the gnome volume control too.

I've also made sure that nothing is muted in both mixers too.

I read that some users had this problem and that it was fixed by doing this, but not for me I'm afraid.

Also, if I run some audio and open the PulseAudio volume control...the level shows as strong...at least internally. 

It's just quiet externally (and it's nothing to do with the speakers or anything because it's all fine in OS X - it's a dual boot system).

Any ideas?

---

### Post by _mario_ on 2008-12-06
> **tedrogers said:**
> 
I have turned up all *relevant* channels on alsamixer and on the gnome volume control too.

I've also made sure that nothing is muted in both mixers too.

I read that some users had this problem and that it was fixed by doing this, but not for me I'm afraid.

Also, if I run some audio and open the PulseAudio volume control...the level shows as strong...at least internally. 

It's just quiet externally (and it's nothing to do with the speakers or anything because it's all fine in OS X - it's a dual boot system).
if this machine has an Intel chipset, then same question as every time ;-): did you add:
```
# fix sound for SantaRosa (Intel chipset) Macs
options snd_hda_intel model=mbp3
```
to /etc/modprobe.d/options?

ciao,
Mario

---

### Post by tedrogers on 2008-12-07
That worked brilliantly.

Quick restart and I have full sound levels!

Thank you Mario!

---

