---
title: "[SOLVED] Silent sound on the new 24&quot; iMac"
date: 2009-05-10
forum: Apple Hardware Users
---

### Post by jhs_proven on 2009-05-10
Hi, Forum. After being sent here by Google for so much troubleshooting, I finally have a chance to share some new info!

I am on a brand new (early May 2009) 24-inch iMac (the lowest-end 24" model). The sound module (snd_hda_intel), ALSA, PulseAudio, and applications all initialize and run fine; however **the system is completely silent**.  None of the information on the web indicates the correct solution.

So here is what I have done, which is working quite well.

[LIST=1]
[*]Contrary to some wikis, there is no more /etc/modprobe.d/options.  Instead, I edited /etc/modprobe.d/alsa-base.conf ...
[*]...and I forced the snd_hda_intel module to use the **lenovo-sky** mode by appended the following: ```
options snd-hda-intel model=lenovo-sky
```
[*]Reboot and it works.
[/LIST]
Next, some questions to the forum:

[LIST=1]
[*]Which wiki page should I update with this information?  (Google has sent  me to a couple of different pages and none of them seem like the canonical, up-to-date, page.)
[*]What information should I gather to identify exactly what hardware I'm on? I'd like for future troubleshooters to be sure that this is the right fix for them? For example:```
$ cat /proc/asound/card0/codec#0 | grep Codec
Codec: Realtek ALC889A
```
[*]Should I pull my edits out of /etc/modprobe.d/alsa-base.conf and place it in a dedicated file? (I'm wondering if a package update will wipe out my changes.)
[*]I still have some small issues with the *volume being lower-than-OSX*, and also that *the headphone jack doesn't work*.  They aren't showstoppers, but I'd love to hear whether people have solved these issues.
[/LIST]

---

### Post by AussieHolden on 2009-05-10
I had full sound in version 8 of Ubuntu but in version 9 the system has dead sound.

Sounds good you could fix it but for someone like me I wouldn't know were to begin to make that change and like you if there is another update this could all be wipped out.

Only an update is going to fix this Apple computers do not change so quickly like PC's do.

---

### Post by cyberdork33 on 2009-05-12
I think there was a patch floating around for this...

I think this is the bug report for you:
[https://bugs.edge.launchpad.net/mactel-support/+bug/346170](https://bugs.edge.launchpad.net/mactel-support/+bug/346170)

If you go here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

It will show you how to properly identify your hardware and lead you to the correct page. Unfortunately, there is not a lot of good info for the iMac like there is for the Macbook(Pro) pages.

---

### Post by knattlhuber on 2009-06-22
Thank you. "model=lenovo-sky" worked beautifully on my 24" iMac (9,1).

---

### Post by dragonleopardpig on 2009-06-22
After searching through the forum, the "model=lenovo-sky" is the only way that can make my imac-20" speakers to work on newly installed Ubuntu 9.04, Thanks!
However, when I tried to play song from mp3 files, the sound seems to be only monotone, no bass at all! It is just too far different from playing in MacOS X.
I believe my aluminum 20" imac 9,1 (bought a month ago) has exactly the same chipset ALC889A. Any help and suggestion on this?
Thanks.

---

### Post by jamesey on 2009-06-23
> **cyberdork33 said:**
> I think there was a patch floating around for this...

I think this is the bug report for you:
[https://bugs.edge.launchpad.net/mactel-support/+bug/346170](https://bugs.edge.launchpad.net/mactel-support/+bug/346170)

If you go here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

It will show you how to properly identify your hardware and lead you to the correct page. Unfortunately, there is not a lot of good info for the iMac like there is for the Macbook(Pro) pages.

whoever was working on that bug seems to have just stopped. He provided a patch but common users like myself don't know how to apply it.

---

### Post by ipina on 2009-07-12
Hi jamesey. Go to [http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147) Hope this helps.

---

### Post by moporoco on 2009-12-15
The lenovo-sky trick fixed the sound on my iMac 24" 9,1 but music sounds like it's coming from a tin can. Much worse than it sounds when running Windows or MacOS. Is there an EQ to fix that or is it a result from this workaround?

---

