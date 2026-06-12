---
title: "My audio is not as loud as it should be."
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by billingsworld on 2007-01-25
Hi,

Using edgy, I have to crank my volume up to max to make it loud enough.  Audio control on panel is max'd.

In System>Preferences>Sound:

I am using Intel 82801BA-ICH2.  Other adapters that can be selected are:

ALSA
ESD
OSS
and autodetect of course

"Sound Events" and "Music and Movies" are set to Intel 82801BA-ICH2.

"Audio Conferencing"
- playback is set to autodetect
- sound capture is set to ALSA

I have checked my cables and such, it's just not loud enough.  Any ideas?  Help me out, I gotta rock!

:guitar: 

Sorry, I added that last bit so I could use the guitar emote. LOL

---

### Post by BarfBag on 2007-01-25
This happens to me sometimes.  Double click on the volume icon in the panel and crank everything up in the volume manager.

---

### Post by billingsworld on 2007-01-25
Is this a common thing in Ubuntu?

---

### Post by BarfBag on 2007-01-25
> **billingsworld said:**
> Is this a common thing in Ubuntu?

From my experience, it's a common problem in most Linux distros.  Kinda annoying.

---

### Post by DSn0wMan on 2007-01-25
Do you have the Intel ICH6 onboard sound? If so it has a bug that needs squashing.

Check out this thread on launchpad.

[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/41015](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/41015)

The only reason I ask, is that your symptoms are similar to what I had going on. In any case if you dont have the Intel ICH6 please disregard my post.

---

### Post by BarfBag on 2007-01-25
> **DSn0wMan said:**
> Do you have the Intel ICH6 onboard sound? If so it has a bug that needs squashing.

Check out this thread on launchpad.

[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/41015](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/41015)

The only reason I ask, is that your symptoms are similar to what I had going on. In any case if you dont have the Intel ICH6 please disregard my post.

I've had the problem in every distro I've tried and have a Realtek-based card.

---

### Post by billingsworld on 2007-01-25
Maybe the problem is related to on-board sound cards.  If someone has a PCI based sound card does the problem present itself?

Perhaps I need a new 5.1 sound system, one that goes to "11"

---

### Post by DSn0wMan on 2007-01-25
No, because the onboard Realtek on my desktop works just fine. However, that chipset performed pretty poorly when I used to run windoze.

---

### Post by Buck2348 on 2007-01-25
I doubt if this has any bearing on your problem, but it took me a while before I learned it.  The volume control you get when you click on the little speaker icon in the panel can be set to control any of a number of tracks or devices.  I couldn't figure out why it had no effect on my system sound volume.  You can right-click on the icon, select "Preferences," and select what you want for it.  I keep mine on "Intel ICH5" (Alsa Mixer) and "Master."

Billingsworld, did you get your sound working better?

Buck

---

### Post by billingsworld on 2007-01-26
Sweet.  Thanks for your post.   For those that want to know!

Right click on the speaker on your main panel.

Select preferences

For me, anyway, select the headphone item in the list (I had it on Master).  AMAZING! I nearly blew my speakers!

If you "Open the volume control", you can select multiple sources and PCM-2 seems to be the magic slide.

Anyway, once you crank out the various inputs/outputs.  Just make sure the headphone slide is up.

Maybe this is a bug?  The Master slide has no effect whereas the headphone output works like a master.  Haha! My wife is going to start yacking at me again!  :lolflag: 

:guitar:

---

### Post by DSn0wMan on 2007-01-26
In my case the headphone worked, but the master did not. After following the instructions in this bug report: 
[https://launchpad.net/ubuntu/+source....15/+bug/41015](https://launchpad.net/ubuntu/+source....15/+bug/41015)

My master volume worked as expected. This becomes important if you need your multimedia buttons to work, as they work on master volume, and not headphone or any other selection.

---

