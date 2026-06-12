---
title: "my sound is gone"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by nonewmsgs on 2007-08-12
well i have a weird intermittant sound error.  every so often my sound up and vanishes.  well the system acts like it's playing, and my volume is all maxed but esd, alsa, and oss all don't produce any sound.  multichannel playback and p16v work.  i dont know why.  this is the 2nd time it's happend and i tried rebooting but nothing is working.

my sound card is a soundblaster audigy2zs computer is 2.4ghz 1gb ram nvidia6600vidcard

---

### Post by wolfen69 on 2007-08-12
it says here [https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs) that it is not supported. however, there *may* be a workaround.

---

### Post by nonewmsgs on 2007-08-12
it works wonderfully 99.9% of the time.  i have left the computer on for several days and all is well including earlier today.  but tonight there's no sound.  the weird thing is when ubuntu is starting i can hear a test audiocard "pfft" when it starts as though it would have sound but the ubuntu drummer is silent and no sound except for the weird types of audio.

---

### Post by nonewmsgs on 2007-08-12
had computer off and turned it back on 5 min later and my drummer is back along with my sound.  maybe it's a heat problem but im using a lot of fans and my system and cpu was only running around 35C (i love zalman cpu fans) but im not monitering that pci card.

---

### Post by fredj on 2007-08-12
The Audigy 2zs is supported in the current version of Alsa. However I don't know why your
sound keeps disappearing. I have a computer with the same sound card and have never 
had this problem.

---

### Post by nonewmsgs on 2007-08-18
it happend again today.  turned on my computer and for a half hour nothing and then real loud my gaim blasted the buddy logging in thing.  weird.

---

### Post by nonewmsgs on 2007-09-06
can this be moved to a more appropriate forum?  it is still unresolved but still intermittant.

---

### Post by nonewmsgs on 2007-09-15
ok my sound was gone all day today.  i went to creative hoping for some binary blob to fix everything but of course not, because creative only caters to windows people.

and i typed lspci and what i found weird wasn't that my soundcard was detected but also that my onboard soundcard was listed!?

```

...
00:0b.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
...
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

```

so i rebooted, went to BIOS to disable my onboard sound, which was already disabled, but i was shocked that linux can still see my disabled stuff.  that's like x-ray eyeglasses or something!  but i also noticed i have my plug-n-play OS disabled.  is that right?

then i rebooted and i sat through fsck and now i have sound.  interestingly lspci still shows my disabled onboard sound.

---

