---
title: "imac g3 seems good ...but"
date: 2005-09-30
forum: Apple PPC Users
---

### Post by cobelloy on 2005-09-30
hi there, I put ubuntu on my daughters g3-350/256meg imac and it was a flawless install and seems nice and responsive even with gnome, but I notice that in the device manager most of the hardware (including the cpu) is not detected, I am a little concerned it is running a bit hot - but how would I know? This mac is a recent purchace and I have only ever had PCs before, I can only-just hear a whirring that starts up from time to time when the hard drive/cdrom are not in use - could that be the cpu fan? Are the temp sensor and fan speed etc set by the software or firmware controlled? Is there some kind of BIOS menu with a mac?
Also, how do I get all the codecs for playing multimedia files? there are less repositories available for the ppc architecture and half the codecs I have on my PC are not available for ppc.
This computer had mac os X and 9 before, X was too slow and 9 was unable to do anything useful (couldn't play videos etc), the most taxing thing I need from this machine is for it to play videos, and I suspect it can, but not without codecs, and I am also concerned about it being left on when its not in use if it is running hot (and it will get left on all day), it was a bargain in super condition and i don't want to wreck it after the previous owner was so careful with it.

I really need some help here - please??

---

### Post by DirtDawg on 2005-09-30
Hmmm. I'm running Ubuntu on a G3 as well with about 100M more RAM. Unfortunately, I can't help you with the tempeature issue. My imac runs Hoary very well and I've had no heating issues. The top of the mac does get very warm to the touch at times, but I have left her running sometimes for days at a time with no ill effects. 
As far as the videos, I've found a player called Gxine which was very easy to install and has run everything I've asked it to thus far (avi, mpegs, etc). If the imac is connected to the internet, it should be available through synaptic (Universe). Otherwise, you can retreive it here (assuming you are using Hoary):
[http://packages.ubuntu.com/hoary/graphics/gxine](http://packages.ubuntu.com/hoary/graphics/gxine)
I hope this might help and good luck.

---

### Post by cobelloy on 2005-09-30
I must be missing something -- gxine doesn't show up on my list in synaptic, could you maybe post a copy of your sources.list for me?

I know I can get it from packages, but the dependancies are insane! I am going to try in the meantime though.

---

### Post by cobelloy on 2005-09-30
OK, I got gxine, and it does seem a bit better, but the sound stops shortly after the movie starts and when it comes back it is badly out of sync and remains that way for the rest of the movie, I try pausing - restarting but it doesn't fix it, DMA is enabled but the cpu is maxed out during playback, perhaps I do need a lighter GUI than gnome after all...

---

### Post by cobelloy on 2005-10-01
OK, this is definately a codec issue, I just got xfce and same problem with movies, but I discovered not all movies, only divx, but I don't know how to get the codecs - it was easy apt-get with my pc but the divx4linux codec is not in my package list with the ppc, likewise the w32codecs package, can someone help please?

---

### Post by Rxke on 2005-10-01
divx4 is quite processor intensive, could be your machine is struggling... i remember having downloaded a divx that did that too, (on an iBook 350MHz G3) so I stopped using it. Recently I downloaded a divx5, though and it ran fine (but that was on OSX) maybe 5 is less process-hungry, i dunno...

About the temp: arguably, if running Xfce, it should run cooler, when idle, of course, playing video will run it hotter, but that's the same oon os9 or X, IMO...

---

### Post by cobelloy on 2005-10-01
well that would make sense - they are divx5 movies, but where do I get the codec from?

---

### Post by cobelloy on 2005-10-01
righto then...

as it happens I do in fact have divx5 for linux codec, not divx4, and I am trying to play divx5 encoded avi movies but the sound stops after about 20sec and only comes back if I advance the position of the movie playback, but then audio is hopelessly out of sync. Am I looking for too much from this little machine, I think it should be able to play some small divx movies shouldn't it?

---

### Post by cobelloy on 2005-10-01
OK, all sorted now, I have returned to my old favourite VLC and it plays the videos flawlessly (once you also install the sound plugins - D'OH!!), so after only a day and a half of hair pulling it is all set up for my little girl. But really, a bit of a hassle but in the end an easy way to get this computer to perform how I had expected it would when I first put in my bid on eBay. And for the record Ubuntu ppc with the gnome desktop totally outperforms mac os X.

thank-you all (once again)

---

### Post by Rxke on 2005-10-01
Good to hear you were successful!

the Ubuntu organisation has this policy not to include non-free codecs, which is ok by me, but it can make it a hassle to figure out where to find them. I think it's in the top three 'issues' re: setup-irritations.

And re:Gnome beating OSX, that's one of the reasons I switched. G3 lacking that velocity engine thingy makes them a bit sluggisch with all that OSX eye-candy, heehee... I was completely amazed to see text scroll really fast on Gnome running Firefox, compared to OSX...

---

### Post by Rxke on 2005-10-01
BTW:
[QUOTE=cobelloy]I can only-just hear a whirring that starts up from time to time when the hard drive/cdrom are not in use - could that be the cpu fan? [/QUOTE]

The iMac 350 [http://www.everymac.com/systems/apple/imac/stats/imac_350.html](http://www.everymac.com/systems/apple/imac/stats/imac_350.html) is convection cooled, does not have any fans. You must be hearing something else then... But what? Maybe former owner was a DIY type that retrofitted a fan somewhere?

---

### Post by jdp on 2005-10-02
I did a retro-fit on my 350 iMac a long time ago.  I just modded it a bit under the removable cover on the bottom to get a fan mounted, and then ran power from the HDD power plug.  If anyone tries the same, make sure the fan blows *UP*.  Otherwise you risk ruining the convection cooling setup and overheating something.  The main advantage to installing a fan is that you get airflow even before the system heats up enough to start convection.  The first fan I tried was a thin 80x80x15 Zalman.  It cooled well, but I couldn't fit the little cover back on.  I later swapped in a 40x40x15 and it fits and lets me leave the cover on.  You can't even tell it's blowing unless it is VERY quiet and you lean close to the back of the machine.  The fan even runs during sleep, so it stays cooled and helps prevent the flyback transformer failure that these are so prone to.

---

