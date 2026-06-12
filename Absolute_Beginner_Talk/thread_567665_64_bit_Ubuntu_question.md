---
title: "64 bit Ubuntu question"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by rdsii64 on 2007-10-04
I am running 32 bit 7.04 now. across my office is a dual core 64 bit machine waiting for me to put Ubuntu on it. My question is about drivers.  

I passed on 64 bit windows because  driver support was spotty at best. will I have have similar problems  with  64 bit  drivers  with a Linux install?

will I have any issues with things like flash plugins  under the 64 bit os ?

will I need 64 bit versions of the required plugins, codecs and media players for dvd play back
ripping dvd's and those kinds of things. 



when I installed 32 bit 7.04 on my 32 bit test bed. it went off with out a hitch. I am hopping the 64 bit install on my  good box will go just as smoothly. 
finding 32 bit versions of those was pretty easy and install was a mouse click
( gotta love apt-get)

Are there any issues I should be aware of.
My hardware is as follows.

dual core AMD64 4200+

a pair of Nvidia 7600 GT's ( I want to run 3 monitors)

2 gigs of dual channel memory

1 500 gig serial ATA drive
1 200 gig parallel ATA drive ( windows install)

Ubuntu will go on my serial ata drive. I will dual boot so I can use my machine to game with windows)

---

### Post by pay on 2007-10-04
You will probably have problems with flash plugins but there are a few workarounds. You can try Gnash, nspluginwrapper or use a 32bit firefox. You can use 64bit codecs that can rip dvds and other videos fine. There hasn't been a file that I've found that 64bit can't play (mplayer, vlc and probably totem can even play wmv)

I think that the 64bit version might even use large amounts of ram better. I think theres a limit to the 32bit version, but can't remember if that limit is 2 gb or 4gb.

---

### Post by rsambuca on 2007-10-04
If your 32bit install went fine, then I suspect it should be the same for the 64bit OS.  There are scripts to install flash and java, so I certainly wouldn't call them "problems" like the previous poster.  Just click it.

---

### Post by nonewmsgs on 2007-10-04
> **rsambuca said:**
> If your 32bit install went fine, then I suspect it should be the same for the 64bit OS.  There are scripts to install flash and java, so I certainly wouldn't call them "problems" like the previous poster.  Just click it.
+1

the first poster isn't trying to mislead you, because in the long long ago, (a version or two) it required more work for those, but now  if you can handle copying and pasting a couple lines into the terminal, you'll be fine. and i would recomend the 64bit.

btw i think it's either 4gb or 8gb

---

### Post by pay on 2007-10-04
> **rsambuca said:**
> There are scripts to install flash and java, so I certainly wouldn't call them "problems" like the previous poster.  Just click it.I will always consider them problems untill we have a fully 64bit flash player under a free license that can play back flash 9. When icedtea and openjava are stable then that will solve the java on amd64 issue (I'm hoping by hardy).

---

### Post by rsambuca on 2007-10-04
> **pay said:**
> I will always consider them problems untill we have a fully 64bit flash player under a free license that can play back flash 9. When icedtea and openjava are stable then that will solve the java on amd64 issue (I'm hoping by hardy).

But there isn't a fully 32bit flash player under a free license that can play back flash 9, so don't make it a 32bit versus 64bit issue.

---

### Post by pay on 2007-10-04
> **rsambuca said:**
> But there isn't a fully 32bit flash player under a free license that can play back flash 9, so don't make it a 32bit versus 64bit issue.I didn't express my feelings correctly. I meant to say that a flash player under a free license. Naturally it will work on 32bit and probably 64bit and other architectures and eliminate our dependency on adobe.

---

### Post by Wynne G Oldman on 2007-10-05
I'd wait until Gutsy is released if I were you, or install the beta version. It automatically asks you if you would like to install any codecs or plugins that you may need. It even installs support for Flash in your 64bit browser. I'm running 64bit Gutsy beta at the moment, and apart from a few bugs, it runs great. I found it easier to install than Fiesty, and I haven't had to use Terminal once. I don't think you should have any more driver problems than you would with the 32bit version.

---

