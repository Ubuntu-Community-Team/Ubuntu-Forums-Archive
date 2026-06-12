---
title: "low audio volume fix"
date: 2008-08-20
forum: Apple Hardware Users
---

### Post by cyberdork33 on 2008-08-20
For those that can't seem to get their audio level high enough on their Mac, a recent submission to the mactel-linux-users list may have revealed the solution.

[COLOR=Red]**NOTE:**[/COLOR] Before using the following, first, run 'alsamixer' in a terminal and make sure that all your channels are unmuted (m-key) and turned up (arrow-keys). After you have tried everything in alsamixer (including switches) then try the below.

[quote=mactel-linux-users]On Mon, 2008-08-18 at 11:10 -0600, Sam Noble wrote:[INDENT]> On Tue, 2008-08-12 at 16:31 +0200, Pol Hallen wrote:[INDENT]> > so, audio runs correctly but the volume sound is too low :-/
> > 
> > I already checked amixer, alsamixer and the volume sounds are at
> > maximum.
> > 
> > Is there a different way to increase the volume?
[/INDENT]> 
> You might check whether or not you are using PulseAudio:
> [http://www.pulseaudio.org/](http://www.pulseaudio.org/)
> 
> If so you'll want to install it's utilities especially:
> $apt-get install pavucontrol
> 
> So that you can adjust the volume there too  :) 
[/INDENT]Pol wrote back and said that it worked; was able to maximize the level using paman.[/quote]

Well, guess what, Hardy uses pulseaudio. So to check the volume level in pulseaudio run:
```
pavucontrol
``` and look in the "Output Devices" tab. You should be able to increase the pulseaudio mixer controls there.

If you want to play with paman, you have to install it.```
sudo apt-get install paman
``` After that, you can run ```
paman
``` and look on the "Devices" tab. You can select the "alsa_output" device under "Sinks" and click properties. Here you should be able to increase the level of the output device (Maybe even past 100% so be careful!).

---

### Post by werthog on 2008-08-20
How convenient, I *just* installed Ubuntu on my MacBook today! I wish there was an easy repository for all the known fixes (touchpad, sound, etc) to make life easier on the Mac.

Anyway, I've got the same quiet sound issue, but unfortunately this fix did not help me; It's already at 100%, and if I crank it higher, it merely distorts it awfully without even raising the volume very much (if at all). Any other ideas?

---

### Post by cyberdork33 on 2008-08-20
> **werthog said:**
> How convenient, I *just* installed Ubuntu on my MacBook today! I wish there was an easy repository for all the known fixes (touchpad, sound, etc) to make life easier on the Mac.

Anyway, I've got the same quiet sound issue, but unfortunately this fix did not help me; It's already at 100%, and if I crank it higher, it merely distorts it awfully without even raising the volume very much (if at all). Any other ideas?
Sorry, was just a try...

Here are the MacBook pages. You should determine the version of yours to find which applies to you.
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

### Post by werthog on 2008-08-20
> **cyberdork33 said:**
> Sorry, was just a try...

Here are the MacBook pages. You should determine the version of yours to find which applies to you.
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

Oh, don't be sorry, every fix doesn't work for everyone :P Thanks for the help anyway!

---

### Post by cyberdork33 on 2008-08-20
> **werthog said:**
> Oh, don't be sorry, every fix doesn't work for everyone :P Thanks for the help anyway!
ah I am more disappointed than anything. I know a lot of people have this problem, and it has not been solved.

---

### Post by werthog on 2008-08-21
> **cyberdork33 said:**
> ah I am more disappointed than anything. I know a lot of people have this problem, and it has not been solved.

Well then good news, I fixed it! After all that fuss, all I had to do was open up the volume control and show all the sliders; turned out "Front" was turned down. I guess I expected that to show up in the settings pages I'd checked by following your post. Anyway, sound's still a little scratchy sometimes but at least I can hear it!

---

### Post by cyberdork33 on 2008-08-21
> **werthog said:**
> Well then good news, I fixed it! After all that fuss, all I had to do was open up the volume control and show all the sliders; turned out "Front" was turned down. I guess I expected that to show up in the settings pages I'd checked by following your post. Anyway, sound's still a little scratchy sometimes but at least I can hear it!ah yes. You should defintely check the mixer levels first (run 'alsamixer' in a terminal). This was directed at those that, even with all the levels at 100% had very low audio levels. I will add a note.

---

### Post by werthog on 2008-08-21
Volume's good, though things are very crackly on the highest settings. Is that unavoidable?

EDIT: Never mind, I got things working nicely now. I followed someone's post on this bug page, after suddenly getting the error there out of nowhere: [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/191027](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/191027)

> 
I managed to solve this by adding:

options snd-hda-intel model=auto

To /etc/modprobe.d/alsa-base, as my hardware was detected as:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

---

### Post by agestrada on 2011-09-17
Same issue with Natty with Macbook Pro 5,5. I fixed it running alsamixer and increasing the volume for the front slider.

---

