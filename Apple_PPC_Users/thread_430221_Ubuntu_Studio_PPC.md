---
title: "Ubuntu Studio PPC?"
date: 2007-05-01
forum: Apple PPC Users
---

### Post by mrbugspray on 2007-05-01
Hey,

does anybody know if there with be an Ubuntu Studio PowerPC? Any help would be much appreciated.

Mr. Bugspray

---

### Post by Ububurns on 2007-05-01
Not sure.  Their website doesn't seem to mention PPC being supported.

What packages are you looking for?

I just made debs for two of the packages included in UbuntuStudio - ardour2 and audacity-gtk2 - if you're interested.

If not... I'm sure you, or someone (me?) could try to make debs for a particular program you are interested in.

---

### Post by stmiller on 2007-05-02
Ubuntu studio will be only for 32bit x86. You can compile a ppc kernel for audio work. You'd do this to increase the kerning timing, and enable a low-latency kernel.

---

### Post by johng4 on 2007-05-02
To be honest.. you can do the following to create your own Ubuntu Studio for PPC (which I will do eventually anyway):

** Download the Realtime-lsm Kernel Patch, and scripts **
This will give your kernel the modules and scripts needed to give users in the "audio" group realtime permissions on processes, as well as an effecient patch to the kernel to allow "realtime" audio processing.

** Install everything JACKit related **
Ok, not everything.. but seriously, nearly everything.  Use discretion.  You MUST get Jack-Rack though.

** Install everything ALSA related **
Again.. use discretion.

** LADSPA, LADSPA, LADSPA... **
Get everything LADSPA.. seriously.. everything.  Even LADCCA.

** Audio Programs **
MIDI - Rosegarden4/Muse
Multitrack Recording - Ardour/Ardour2
Mixing & DJing - TermintorX, Mixxx, qsampler
D.A.W. - Jokosher
Recording - Rezound, optionally Audacity (I perfer rezound)
Mastering - JAMin

Utility Programs: qsynth, vkeyb, and all sorts of mixers (pick the ones you like).

** Trim the fat **
1) Get Fluxbox, and learn how to use it.  Its the single best way to get the most out of your resources.  If fluxbox is too complicated (seriously, its not.. spend an hour on the docs.. you'll master it) get XFCE.  Gnome is nice, but its still got some bloat to it.  KDE4 maybe.. but until thats a reality and we see the resource meters for ourselves, don't.  Fluxbox is the best, and if you open up a system monitor and compare it to gnome/kde/xfce.. you'll see why.  Avoid Enlightenment... its nice, dont get me wrong, but its not stable enough to rely on when it comes down to producing something worthwhile.

2) Remove/Turnoff services you don't need.  CUPS is one of the biggest ones.  You won't need a printer per se, so shut 'er off.  Optimally you want only the absolute essentials running.

3) No fancy effects. If you go the fluxbox route, its already done for you.. if you go the XFCE route, avoid the temptation of compiz/beryl.  They aren't "hogs" per se, but they aren't friendly to audio apps trying to set themselves to RT priority.


** RTFM **
Audio programs are no joke.  Ardour, and Rosegarden are not for beginners.  Your life will suck if you don't read documentation.  So, download the pdf's, html's, and whatever else you can find.


Outside of that.. PPC Studio is just a [remastersys]("http://www.linuxmint.com/wiki/index.php/Remastersys") away.

:guitar:

---

### Post by stmiller on 2007-05-03
> **johng4 said:**
> To be honest.. you can do the following to create your own Ubuntu Studio for PPC (which I will do eventually anyway):

** Download the Realtime-lsm Kernel Patch, and scripts **
This will give your kernel the modules and scripts needed to give users in the "audio" group realtime permissions on processes, as well as an effecient patch to the kernel to allow "realtime" audio processing.


That realtime-lsm package does not instantly give you a realtime-enabled kernel. If you read the doc about that package you still have to recompile your kernel. And it is obsolete now, since the current kernels have realtime built in.

BUT Ubuntu does not enable these things by default. And the kernel timing is set too low by default. You have to bump that up for rosegarden and others to work properly, and enabled the preemt kernel.

---

### Post by johng4 on 2007-05-03
> **stmiller said:**
> That realtime-lsm package does not instantly give you a realtime-enabled kernel. If you read the doc about that package you still have to recompile your kernel.

Must have self-editted that part out.  I am aware that it requires re-compiling the kernel.  I was not aware that the newer kernels include realtime preemption in them.  

Either way.. point remains, with the listed packages, and the realtime/multimedia kernel, voila.. Ubuntu PPC Studio.  Would be nice to see it run on one of those $10k Power Macs with 16GB of ram, and dual quad-core cpus.  Then again with that much processing power and memory.. do you even need realtime? (rhetorical)

---

### Post by discoandy on 2007-05-04
of the audio programs you talked about, do you know if any of them are similar to Adobe Audition?

---

### Post by mrbugspray on 2007-05-04
> **johng4 said:**
> To be honest.. you can do the following to create your own Ubuntu Studio for PPC (which I will do eventually anyway):

** Download the Realtime-lsm Kernel Patch, and scripts **
This will give your kernel the modules and scripts needed to give users in the "audio" group realtime permissions on processes, as well as an effecient patch to the kernel to allow "realtime" audio processing.

** Install everything JACKit related **
Ok, not everything.. but seriously, nearly everything.  Use discretion.  You MUST get Jack-Rack though.

** Install everything ALSA related **
Again.. use discretion.

** LADSPA, LADSPA, LADSPA... **
Get everything LADSPA.. seriously.. everything.  Even LADCCA.

** Audio Programs **
MIDI - Rosegarden4/Muse
Multitrack Recording - Ardour/Ardour2
Mixing & DJing - TermintorX, Mixxx, qsampler
D.A.W. - Jokosher
Recording - Rezound, optionally Audacity (I perfer rezound)
Mastering - JAMin

Utility Programs: qsynth, vkeyb, and all sorts of mixers (pick the ones you like).

** Trim the fat **
1) Get Fluxbox, and learn how to use it.  Its the single best way to get the most out of your resources.  If fluxbox is too complicated (seriously, its not.. spend an hour on the docs.. you'll master it) get XFCE.  Gnome is nice, but its still got some bloat to it.  KDE4 maybe.. but until thats a reality and we see the resource meters for ourselves, don't.  Fluxbox is the best, and if you open up a system monitor and compare it to gnome/kde/xfce.. you'll see why.  Avoid Enlightenment... its nice, dont get me wrong, but its not stable enough to rely on when it comes down to producing something worthwhile.

2) Remove/Turnoff services you don't need.  CUPS is one of the biggest ones.  You won't need a printer per se, so shut 'er off.  Optimally you want only the absolute essentials running.

3) No fancy effects. If you go the fluxbox route, its already done for you.. if you go the XFCE route, avoid the temptation of compiz/beryl.  They aren't "hogs" per se, but they aren't friendly to audio apps trying to set themselves to RT priority.


** RTFM **
Audio programs are no joke.  Ardour, and Rosegarden are not for beginners.  Your life will suck if you don't read documentation.  So, download the pdf's, html's, and whatever else you can find.


Outside of that.. PPC Studio is just a [remastersys]("http://www.linuxmint.com/wiki/index.php/Remastersys") away.

:guitar:

Thanks... I added a real-time kernel instead of a low latency kernel. Then I added all the ubuntu studio packages that are already up...

---

