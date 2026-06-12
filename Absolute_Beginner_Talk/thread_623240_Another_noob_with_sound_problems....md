---
title: "Another noob with sound problems..."
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by David Goodier on 2007-11-25
Hi there. I know similar posts have gone before, and I have tried to trawl the forums, but to no avail!

I eventually got fed up with windows XP bloating out the 20GB partition on my sony vaio PCG-TR5MP (known as TR3A in the US I beleive). I do like the laptop as it is tiny enough to carry with me, and the equivalent size new laptop is about £1,500, so I decided it is about time I dabbled in a smaller, more efficient operating system...

I ripped out Windows XP last night and installed Ubuntu on a single 40GB partition. My theory was the best way to learn Linux was to just immerse myself in it, so no Dual Boot options, completely fresh installation!

Doubtless I'll learn tweaks to get the correct buttons working; so far it's useable, wireless up no problem, USB working, memory stick drive and CD working OK.The standby option occasionally gives me what I have learned is the 'black screen of death', but so far it has been an entertaining 2 days!

The problem I can't work out is the lack of sound...

I can hear about 30% of the 'normal' level through the headphone socket, but noting through the inbuilt speakers from any program.

lspci tells me that I have an Intel 8280 1DB-CH4 chipset, which is correct according to the Sony website.
The ALSA mixer recognises this as the enabled device, and has a volume control and mixer panel (not muted, sliders to max)

Copied from lspci:
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

I really don't know where to go next; I am a total noob having used Windows since 3.0, and it's a long time since DOS based 'secretary bird', and even longer since sellotaping the 32k RAM pack on my Sinclair ZX81!!

HEEEELP!

David Goodier

---

### Post by DutyDuty on 2007-11-25
Now, I didn't see your model of computer in your post (sorry if I missed it).

If it's a Toshiba, try the link in my sig. If not, is everything with alsamixer okey-dokey?

---

### Post by David Goodier on 2007-11-25
Thanks, it was lost among the blurb...Sony Vaio TR5

ALSA mixer seems to work - if I double click on the icon it says in the bar at the top: Volume control: INTEL 8280 1DB-ICH4(ALSA mixer)

If I type alsamixer in terminal it comers up with all the sliders to max. and reports the same card (and the AD1981B chipset)

The AD1981B is mentioned on thinkwiki.org as being a conflict with the headphone output on thinkpads; tried muting that with no benefit.

Sound output to speakers is set to max in BIOS

Still nothing (no system sound on startup, no sound in any sound-enabled program)

I'm stumped!

David

---

### Post by wormser on 2007-11-25
I am dealing with a similar sound issue.  The external amplifier option can cause this.  Try this:  double click on the sound icon> switches tab> turn external amplifier on or off.  If you do not see the switches tab then edit> preferences> check every box.

The second thing to try is in this [thread]("http://ubuntuforums.org/showthread.php?t=314383").

I still have not solved mine yet but those are 2 things that I have found to help others with similar issues.  Good luck.

---

